# Метод оцифровки pdf таблиц

| Название файла/директории | Содержание файла |
|----:|:----------|
| Метод извлечения таблиц из отчетности ЦБ.ipynb | Скрипт для конвертации таблиц из файла pdf в файл xlsx|
| Исходный файл | Директория, содержащая Статистический бюллетень Банка России в расширении .pdf |
| Таблицы | Директория, содержащая извлеченные таблицы из исходного файла|

## Описание 

Метод извлечения таблиц из отчетности ЦБ представляет собой способ транспортировки данных статистического бюллетеня России в удобный для анализа формат. Метод позволяет выгрузить данные типа float в .xlsx с обозначением месяца и года(тип string) в столбце таблицы. Код ломается, если цифры в таблице разделены пробелами. В остальных случаях скрипт работает корректно. Запуск осуществляется в Jupyter Notebook или Google Collab. 

## Документация

* [Документация по работе с Python](https://www.python.org/)
* [Документация по работе с библиотекой Tabula](https://tabula-py.readthedocs.io/en/latest/tabula.html)
* [Документация по работе с библиотекой Pandas](https://pandas.pydata.org/pandas-docs/stable/index.html)

## Установка

1) Для настройки необходимых пакетов python для скрипта введите в командной строке:

> pip install -r "requirements.txt"

2) Затем необходимо выполнить последовательный запуск блоков кода с функциями:    
*get_slice_header_index(df) принимает на вход сырой датафрейм, производит поиск последней строки шапки и возвращает индекс этой строки;    
*df_with_year(df) принимает на вход тот же необработанный датафрейм и производит его обработку. Внутри запускается функция get_slice_header_index(df). Производится обрезка шапки и датафрейма по годам. Возвращает список, состоящий из предобработанных датафреймов;    
*create_df(df_year) принимает на вход предобработанный датафрейм. Добавляет столбец с датой. Возвращает полученный датафрейм;    
*result_table(pages) принимает на вход страницы для оцифровки. Функция выполняет чтение таблицы и создает датафрейм, который в последствии передается в функции df_with_year(df) и create_df(df_year). Готовый датафрейм записывается в excel файл.    
*main(pages_to_convert) принимает на вход список, состоящий их страниц с необходимыми таблицами(номер страницы формата int или список, если таблица разделена на несколько страниц). Генерит название excel файла и вызывает функцию result_table(pages).    

3) В следующем блоке находятся переменные, которые необходимо изменить пользователю:    
*pages_to_convert - переменная типа list. В неё необходимо ввести страницы таблиц для оцифровки. Если таблица расположена на одной странице, то добавляется объект int, если таблица разделена на несколько страниц, то добавляется список, включающий номера страниц типа int.     
*path_to_file - переменная типа string. В неё необходимо вписать название пути, в котором содержится pdf файл для оцифровки.    

4) После ввода необходимых данных нужно запустить последний блок кода. После отработки всех функций оцифрованные таблицы можно будет найти в папке "Таблицы".


## :shipit: Контакты
**Telegram** @niii_chel_angelo    
**ВКонтакте** [niii_popova](https://vk.com/niii_popova)    
**Email** PopovaNinaM@yandex.ru    
