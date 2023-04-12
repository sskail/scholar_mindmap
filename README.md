# Google Scholar Collaboration Network

Этот проект предназначен для парсинга страниц Google Scholar авторов и создания графа сотрудничества между их организациями.

## Описание кода

В коде реализованы следующие классы и функции:

- `class Connector`: Класс, отвечающий за парсинг страниц Google Scholar и поиск совместных работ авторов.
  - `__init__(self)`: Конструктор класса Connector.
  - `parser(self, part_url)`: Метод для парсинга страницы Google Scholar с помощью BeautifulSoup.
  - `start(self, collaber_link, max_deep=0)`: Метод для запуска парсинга.
  - `pars(self, max_deep)`: Метод для поиска совместных работ на страницах Google Scholar сотрудников.
  - `find_collabers(self, resp, collaber_main, current_deep)`: Метод для поиска совместных работ на странице Google Scholar сотрудника.

- `format(text)`: Функция форматирования для объединения компаний.
- `filter_data_for_graph(unfiltred_data)`: Функция для фильтрации данных перед построением графа.

## Как использовать

1. Импортируйте класс `Connector`.
2. Создайте экземпляр класса `Connector` и вызовите метод `start` с ссылкой на страницу автора Google Scholar и максимальным уровнем вложенности.
3. Фильтруйте полученные результаты с помощью функции `filter_data_for_graph`.
4. Визуализируйте граф сотрудничества, используя библиотеку igraph.

Пример использования:

```python
link = ('/citations?hl=ru&user=tMY31_gAAAAJ')
Parser = Connector()
Parser.start(link, max_deep=1)
coauthor_data = filter_data_for_graph(Parser.res_mass)

# ... (построение графа с использованием igraph)
