### Распознавание эмоций по лицу с использованием CNN

##### Обработка данных

- Изображения из `facial-expression-recognition-dataset`.
- Использование `ImageDataGenerator` из библиотеки Keras для извлечения признаков, включая масштабирование, вращение и другие трансформации для улучшения вариативности входных данных.
- Преобразование значений пикселей из диапазона (0, 255) в диапазон (0, 1) и изменение размера изображений до 48x48.
- Преобразование изображений в оттенки серого для фокусировки на структуре и особенностях лица вместо цвета, который меньше влияет на эмоции человека.

##### Архитектура модели

- Использование слоев Conv2D с матрицами ядер размером 5x5 и 3x3, увеличивая количество фильтров от 64 до 256.
- Применение батч-нормализации и максимальной пулинга для снижения переобучения.
- Использование Dropout для уменьшения переобучения путем случайного удаления некоторых узлов.
- Последний полносвязанный слой с 7 узлами и функцией активации softmax для классификации эмоций.

##### Результат

- Разделение данных на обучающую и тестовую выборки (80% - 20%).
- Использование алгоритма обратного распространения и оптимизационного алгоритма Adam для нахождения оптимальных параметров модели.
- Оценка модели на тестовой выборке с предсказанием эмоций изображения.

### Распознавание эмоций по лицу с использованием DCNN

##### Подготовка данных

- Загрузка и обработка данных из `facial-expression-recognition`.
- Использование `ImageDataGenerator` для выполнения различных трансформаций изображений, таких как вращение, масштабирование и другие, для увеличения разнообразия входных данных.
- Масштабирование значений пикселей из (0, 255) в (0, 1) и изменение размера изображений до 48x48.
- Преобразование изображений в оттенки серого для фокусировки на структуре и особенностях лица.

##### Построение модели DCNN

- Использование слоев Conv2D с фильтрами размером 5x5 и 3x3, увеличивая количество фильтров от 64 до 256.
- Применение батч-нормализации и максимальной пулинга для снижения переобучения и уменьшения размера матрицы признаков.
- Использование Dropout для предотвращения переобучения путем случайного удаления некоторых узлов.
- Последний полносвязанный слой с 7 узлами, каждый из которых соответствует типу эмоции, и использование softmax для классификации.

##### Обучение модели

- Разделение данных на обучающую и проверочную выборки (80% - 20%).
- Использование алгоритма обратного распространения и оптимизационного алгоритма Adam для нахождения оптимальных параметров модели.
- Обучение модели и оценка ее производительности на проверочной выборке.

### Распознавание эмоций по голосу с использованием CNN

##### Чтение и Преобразование данных

- Использование библиотеки `librosa` для чтения и преобразования аудиоданных.
- `librosa.load(path, duration=duration, offset=offset)` для чтения аудиофайла и преобразования его в числовой массив.
- Преобразование аудио в числовой формат, включая параметры, такие как zcr, rmse, mfcc.
- Нормализация данных с разделением на обучающий и тестовый наборы, а затем стандартизация с использованием `StandardScaler`.

##### Выделение признаков

- Использование сверточных слоев с фильтрами размером 1x5 и 256 фильтрами.
- Обучение сверточной сети с использованием алгоритма обратного распространения и оптимизационного алгоритма Adam для поиска оптимальных параметров.

##### Классификация

- Применение LSTM (Long Short-Term Memory) для классификации.
- Использование ворот, таких как Forget gate, Input gate, и Output gate.
- Поиск оптимальных параметров для каждого ворота с использованием обратного распространения и оптимизационного алгоритма Adam.
- Получение модели с точностью около 55% - 60%.

### Распознавание эмоций по голосу с использованием LSTM

##### Чтение данных

- Получение данных из набора данных `facial-expression-recognition-dataset`.
- Использование `ImageDataGenerator` от Keras для автоматической загрузки и предобработки изображений.
- Изменение размера изображений до 48x48 пикселей и преобразование их в оттенки серого.

##### Обработка данных

- Чтение данных из CSV-файла и нормализация аудиосигнала до числового формата.
- Вставка нулей в случайных ячейках для выравнивания длины каждого аудиофайла.
- Получение меток и преобразование их в one-hot вектора для классификации с использованием CNN.

##### Нормализация данных

- Разделение данных на обучающую и тестовую выборки.
- Нормализация данных с использованием `StandardScaler` для поддержания значений в пределах [-1, 1].
- Использование `np.expand_dims` для добавления размерности к матрице и соответствия входным данным CNN.

##### Поиск характеристик

- Создание модели CNN с использованием Conv1D с 16 фильтрами и размером ядра 3.
- Применение обратного распространения и оптимизационного алгоритма Adam для настройки параметров фильтров.

##### Классификация

- Использование LSTM для классификации.
- Поиск оптимальных параметров для ворот, таких как Forget gate, Input gate и Output gate, с использованием обратного распространения и оптимизационного алгоритма Adam.
- Получение модели с точностью около 55% - 60%.
