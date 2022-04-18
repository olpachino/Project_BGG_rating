# Итоговый проект.  
## Предсказание рейтинга настольных игр, на основании данных [BGG](https://boardgamegeek.com/) 
### Школа Skill Factory 

## Оглавление  
[1. Постановка цели и описание данных](https://github.com/olpachino/Project_BGG_rating/blob/master/README.md#Постановка цели и описание данных)  
[2. Краткая информация о данных](https://github.com/olpachino/Project_BGG_rating/blob/master/README.md#Краткая-информация-о-данных)  
[3. Этапы работы над проектом](https://github.com/olpachino/Project_BGG_rating/blob/master/README.md#Этапы-работы-над-проектом)  
[4. Результат](https://github.com/olpachino/Project_BGG_rating/blob/master/README.md#Результат)  

### Постановка цели и описание данных  

**Данные:** [данные](https://www.kaggle.com/datasets/caesuric/bgggamesdata) взяты с платформы Kaggle, данные о рейтинге настольных игр с сайта [BGG](https://boardgamegeek.com/)

**Цель:** предсказать рейтинг настольной игры и понять, какие признаки оказывают на него сильнейшее влияние.

Данные уже содержат в себе ***rating***, так что задача относится к классу задач Машинного обучения с учителем, и предсталяет собой построение регрессии:

- **Обучение с учителем:** у нас есть как все необходимые признаки, на основе которых выполняется предсказание, так и сам целевой признак.
- **Регрессия:** будем считать, что рейтинг настольной игры - это непрерывная величина.

В конечном итогенужно построитькак можно более точную модель, которая на выходе дает легкоинтерпретируемые результаты, то есть мы сможем понять на основании чего модель делает тот или иной вывод.  

**Метрика качества**
Результаты оцениваются по метрике MAE.  
MAE расшифровывается выражение как cредняя абсолютная ошибка.  
Это функция потерь, используемая в регрессионных моделях. MAE - это сумма абсолютных значений разностей между целевой переменной и переменной-предиктором. Следовательно, он измеряет средний размер ошибки в наборе прогнозов независимо от направления ошибки. Диапазон потерь также составляет от 0 до ∞.
<img src="https://images2.russianblogs.com/287/85/858abf653512e1ebe9fda8727b5de3f7.png" />
  
:arrow_up:[к оглавлению](https://github.com/olpachino/skillfactory_rds/blob/master/module_6/README.md#Оглавление)

### Краткая информация о данных
На [платформе](https://www.kaggle.com/datasets/caesuric/bgggamesdata) доступно несколько собранных датасетов. Для своей работы мы возьмем основной [basic_data.]()
В [датасете]() собраны данные о 286186 настольных игр.

На платформе описания признаков нет, поэтому постараемся самостоятельно описать признаки:

1. **name** - название настольной игры
0. **description** - описание настольной игры
0. **thumbnail** - миниатюра
0. **image** - изображение
0. **rating** - рейтинг, наша целевая переменная
0. **bayes_rating** - байесовский рейтинг
0. **usersrated** - кол-во голосов
0. **bggrank** - ранг BGG
0. **stddev** - стандартное отклонение
0. **owned** - кол-во владельцев игры
0. **trading** - кол-во продающих
0. **wanting** - кол-во пользователей, желающих сыграть в игру
0. **wishing** - кол-во пользователей, желающих приобрести игру
0. **numweights** - кол-во пользователей, указавших вес игры (сложность)
0. **averageweight** - средний вес игры (сложность)
0. **yearpublished** - год выпуска игры
0. **minplayers** - минимальное кол-во игроков
0. **maxplayers** - максимальное кол-во игроков
0. **playingtime** - игровое время партии (обычно указывается производителем)
0. **minplaytime** - минимальное время партии
0. **maxplaytime** - максимальное время партии
0. **age** - минимальный возраст игроков

:arrow_up:[к оглавлению](https://github.com/olpachino/skillfactory_rds/blob/master/module_6/README.md#Оглавление)

### Этапы работы над проектом  

В общем случае процесс решения задач возникающих в Машинном обучении состоит из следующих этапов:

1. Очистка и форматирование данных
2. Предварительный анализ данных
3. Выбор наиболее полезных признаков и создание новых более репрезентативных
4. Сравнение качества работы нескольник моделей
5. Оптимизация гиперпараметров в лучшей модели
6. Проверка модели на тестовой выборке
7. Интерпретация результатов
8. Итоговое представление результатов работы
:arrow_up:[к оглавлению](https://github.com/olpachino/skillfactory_rds/blob/master/module_6/README.md#Оглавление)

### Результат  
Была сделана довольно большая работа по обработке признаков. Найдены зависимости в признаках и отобраны значимые.
Подбор моделей: на примере простой модели LinearRegression, MAE = 27.29%, строились выводы об успешности моделей.  
RandomForestRegressor, MAE: 10.75%  
CatBoost, MAE: 10.92%  
BaggingRegressor с RandomForestRegressor, MAE: 10.77%
GradientBoostingRegressor, MAE: 11.86%  
Лучший результат дала модель Stacking with RandomForestRegressor and CatBoostRegressor, MAE: 10.69%

К сожалению подбор гиперпараметров через GridSearchCV не удался, не хватило вычислитеной мощности оборудования.
:arrow_up:[к оглавлению](https://github.com/olpachino/skillfactory_rds/blob/master/module_6/README.md#Оглавление)
