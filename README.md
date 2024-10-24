# Аналитик данных | Karpov Courses

В этот репозиторий я выгрузила юпитер ноутбуки с заданиями, которые делала в ходе прохождения курса по аналитике данных, а также файлы с исходными данными к ним.

## Подробнее о заданиях
### [1. Первый проект (папка first_project)](https://github.com/val-asoskova/karpov-courses-data-analytics/tree/main/first_project)
Первый промежуточный проект в обучении.\
В этом задании требовалось проанализировать данные о заказах в интернет-магазине: 
1. Посчитать количество пользователей.
2. Посчитать количество недоставленных заказов.
3. Определить день недели с наибольшим количеством покупок для каждого товара.
4. Посчитать сколько у каждого пользователя в среднем покупок в неделю (по месяцам).
5. Выполнить когортный анализ.
6. Выявить когорту с самым высоким retention на 3-й месяц в период с января по декабрь.
7. Построить rfm-сегментацию.

Файлы с исходными данными (более подробное описание полей см. в [юпитер ноутбуке](https://github.com/val-asoskova/karpov-courses-data-analytics/blob/main/first_project/first_project.ipynb)):
* [olist_customers_dataset.csv](https://github.com/val-asoskova/karpov-courses-data-analytics/blob/main/first_project/olist_customers_dataset.csv) — таблица с уникальными идентификаторами пользователей
* [olist_orders_dataset.csv](https://github.com/val-asoskova/karpov-courses-data-analytics/blob/main/first_project/olist_orders_dataset.csv) —  таблица заказов
* [olist_order_items_dataset.csv](https://github.com/val-asoskova/karpov-courses-data-analytics/blob/main/first_project/olist_order_items_dataset.csv) —  товарные позиции, входящие в заказы

В результате у меня получился достаточно объёмный ноутбук, в котором я последовательно ответила на каждый из вопросов. Помимо кода ноутбук также содержит комментарии с моими рассуждениями во время решения этих задач.

### [2. Практическое задание по статистике. Кейс №2](https://github.com/val-asoskova/karpov-courses-data-analytics/tree/main/ab_tests)
Практический кейс из модуля "Статистика".\
В этом задании требовалось оценить эффективность новой системы рекомендаций товаров для приложения по доставке продуктов с помощью анализа результатов A/B-теста. 

Файлы с исходными данными:
* [ab_users_data](https://github.com/val-asoskova/karpov-courses-data-analytics/blob/main/ab_tests/ab_users_data.csv) – история заказов пользователей, в этой таблице есть информация о том, какие заказы создавали и отменяли пользователи
* [ab_orders](https://github.com/val-asoskova/karpov-courses-data-analytics/blob/main/ab_tests/ab_orders.csv) – подробная информация о составе заказа, тут для каждого заказа есть список id тех продуктов, которые были включены в заказ
* [ab_products](https://github.com/val-asoskova/karpov-courses-data-analytics/blob/main/ab_tests/ab_products.csv) – подробная информация о продуктах, их название и стоимость

В качестве рассматриваемых метрик я использовала среднее количество продуктов в заказе, средний чек и % отмен. Изучила данные, сформировала датафреймы для каждой из рассматриваемых метрик, проверила получившиеся выборки на нормальность и гомогенность дисперсий, затем воспользовалась t-тестом (для среднего количества продуктов в заказе и среднего чека), а также критерием Хи-квадрат (для % отмен) для определения наличия статистической значимости в различиях между выборками (см. [ноутбук](https://github.com/val-asoskova/karpov-courses-data-analytics/blob/main/ab_tests/case_2.ipynb)).\
В ходе изучения выяснила, что среднее количество продуктов в заказе и средний чек имеют статистически значимое отличие (обе метрики выросли для тестовой группы с новой системой рекомендаций), а % отмен статистически значимо не отличается.\
Таким образом, я сделала вывод о том, что, при условии схожести пользователей в контрольной и тестовой группе (то есть при условии того, что алгоритм сплитования был честным), новая система рекомендаций принесла пользу бизнесу, её стоит выкатить на всех пользователей.

### [3. Финальный проект курса](https://github.com/val-asoskova/karpov-courses-data-analytics/tree/main/final_project)
Финальный проект, по итогам выполнения которого курс считался пройденным и усвоенным.\
В этом задании требовалось исследовать несколько аспектов мобильного приложения:
1. Написать функцию для подсчёта retention.
2. Оценить результаты A/B теста наборов акционных предложений, сформулировать выводы об эффективности того или иного набора.
3. Предложить метрики для оценки результатов ивентов в мобильной игре.

Файлы с исходными данными:
* [problem1-reg_data.csv](https://github.com/val-asoskova/karpov-courses-data-analytics/blob/main/final_project/problem1-reg_data.csv) – данные о времени регистрации
* [problem1-auth_data.csv](https://github.com/val-asoskova/karpov-courses-data-analytics/blob/main/final_project/problem1-auth_data.csv) – данные о времени захода пользователей в игру
* [problem2-ab_data.csv](https://github.com/val-asoskova/karpov-courses-data-analytics/blob/main/final_project/problem2-ab_data.csv) – данные A/B теста

Для выполнения задания 1 я написала две функции:\
– одна считает ретеншн по дням (с вводом количества дней и года, за который необходимо построить ретеншн) и выводит результат в виде графика.
– вторая считает ретеншн общепринятым образом через когорты и визуализирует результат в виде тепловой карты.

В ходе выполнения задания 2 я изучила данные пользователей в обеих группах, посчитала разницу в доходе, ARPU и ARPPU между ними, посмотрела на минимальный и максимальный чек в обеих группах. Таким образом я выяснила, что данные двух групп очень сильно различаются по доходным метрикам: в тестовой группе сумма покупок пользователей варьировалась от 2000 до 4000, в то время, как в контрольной — от 200 до 37433. При этом большая часть пользователей в контрольной группе имели минимальную сумму покупки (от 200 до 400), однако 123 пользователя из этой группы имели суммы покупок, превышающие 35000. Что уже очень подозрительно и говорит о том, что тест был проведён некорректно, алгоритм сплитования не был честным, и в группы попали люди, очень отличающиеся по характеристикам.\

Однако я решила продолжить изучение данных (в том числе для того, чтобы продемонстрировать свои навыки, конечно же).\
В качестве изучаемых метрик я выбрала ARPU, ARPPU и CR.\
Проверила данные на нормальность с помощью метода выборочных средних и ЦПТ, так как нормальность требуется проверять именно у выборочных средних исследуемого признака, а не у самих исходных данных. Обе выборки оказались нормальными.\
Далее проверяла равенство дисперсий (тест Левена) и проводила тесты. Вот что получилось:
* Для ARPU: дисперсии однородны, но гипотеза о наличии статистически значимых различий между ARPU в двух группах не подтвердилась. Проверяла классическим t-тестом.
* Для ARPPU: дисперсии неоднородны, гипотеза о наличии статистически значимых различий между ARPPU в двух группах также не подтвердилась. Проверяла t-тестом с поправкой Уэлча на негомогенность дисперсий.
* Для CR: так как метрика является категориальной (пользователь или платящий (1) или нет (0)), то её стат-значимость проверялась критерием Хи-квадрат. Тест показал наличие статистически значимых различий в конверсии в двух группах.\
Подсчитанной конверсией была ~0.95% в контрольной и ~0.89% в тестовой, при этом тест подтвердил, что это статистически значимое различие. То есть конверсия в тестовой группе стала хуже, и это не случайность. Следовательно, мы не можем считать набор акционных предложений для тестовой группы лучшим.\

Список метрик для выполнения задания 3 можно посмотреть в [ноутбуке](https://github.com/val-asoskova/karpov-courses-data-analytics/blob/main/final_project/final_project_var1.ipynb).
