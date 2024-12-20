# Учебен проект N2
## Соларни паркове

### Описание на проекта:
Компания за оценка и внедряване на соларни системи, иска да разработи система за оценка на 
възможностите на определена географска територия за нуждите на соларната индустрия. Компанията работи с клиенти, за които се подготвят проекти. Всеки проект е свързан с едно или повече лица за контакт. 

Всеки един от проектите включва в себе си оценка на георгафска територия и специфично оборудване, което
може да бъде инсталирано в рамките на тази територия. Клиентите, могат да получат информация за цялостния разход, за всеки един от проектите, както и такава за специфична локация. 


### Модел на задачата:
**Клиентите** в приложението са дефинирани със следните атрибути:
<table>
    <tr>
        <td width="200">id</td>
        <td width="800">Уникален идентификатор (автоматично генериран от системата)</td>
    </tr>
    <tr>
        <td width="200">name</td>
        <td width="800">Име на клиента</td>
    </tr>
    <tr>
        <td width="200">Number of open projects</td>
        <td width="800">Брой на проектите, на конкретен клиент</td>
    </tr>
</table>


**Проектите** в приложението са дефинирани със следните атрибути:
<table>
    <tr>
        <td width="200">id</td>
        <td width="800">Уникален идентификатор (автоматично генериран от системата)</td>
    </tr>
    <tr>
        <td width="200">name</td>
        <td width="800">Име на клиента</td>
    </tr>
    <tr>
        <td width="200">cost</td>
        <td width="800">Разходи направени по проекта</td>
    </tr>
</table>

**Контакти** в приложението са дефинирани със следните атрибути:
<table>
    <tr>
        <td width="200">id</td>
        <td width="800">Уникален идентификатор (автоматично генериран от системата)</td>
    </tr>
    <tr>
        <td width="200">first name</td>
        <td width="800">Първо име на контакта</td>
    </tr>
    <tr>
        <td width="200">last name</td>
        <td width="800">Фамилия на контакта</td>
    </tr>
    <tr>
        <td width="200">phone</td>
        <td width="800">Телефонен номер</td>
    </tr>
    <tr>
        <td width="200">email</td>
        <td width="800">Е-mail адрес</td>
    </tr>
</table>

**Оценките за територията** в приложението са дефинирани със следните атрибути:
<table>
    <tr>
        <td width="200">id</td>
        <td width="800">Уникален идентификатор (автоматично генериран от системата)</td>
    </tr>
    <tr>
        <td width="200">name</td>
        <td width="800">Название на оценяваната територия</td>
    </tr>
    <tr>
        <td width="200">address</td>
        <td width="800">Адресс на територията</td>
    </tr>
    <tr>
        <td width="200">Configuration cost</td>
        <td width="800">Разход за оборудване</td>
    </tr>
    <tr>
        <td width="200">Other cost</td>
        <td width="800">Други разходи</td>
    </tr>
</table>

<code>
Описаните модели, са предварително съгласувани с клиента - важно е да анализираме и обсъдим, дали е необходими да добавим допълнителни връзки между описаните модели
</code>


### Предварително известни API Ендпойнти:
**Потребители**:
- `GET      /customers`
- `GET      /customers/:id`
- `POST     /customers`
- `PUT      /customers/:id`
- `DELETE   /customers/:id`

**Проекти**:
- `GET      /projects`
- ??? Всички проекти свързани с даден клиент
- `GET      /projects/:id`
- `POST     /projects`
- `PUT      /projects/:id`
- `DELETE   /projects/:id`

**Контакти**:
- `GET      /contacts`
- ??? Всички контакти свързани с даден проект
- `GET      /contacts/:id`
- `POST     /contacts`
- `PUT      /contacts/:id`
- `DELETE   /contacts/:id`

**Оценявани територии**:
- `GET      /sites`
- ??? Всички територии свързани с даден проект
- `GET      /sites/:id`
- `POST     /sites`
- `PUT      /sites/:id`
- `DELETE   /sites/:id`


## Нефункционални изисквания:
- Приложението трябва да следва **RESTful принципи** и да използва подходящи HTTP методи (GET, POST, PUT, DELETE).
- Използвайте H2 база данни, за съхранение на данните, получени от приложението
- Проектът трябва да бъде разработен с помощта на **Spring Boot** и да използва неговите вградени компоненти за обработка на REST API.
- Обработката на грешки трябва да връща смислени съобщения и HTTP статус кодове (напр. 400 Лоша заявка, 404 Не е намерено).
- Изтриването на данните, трябва да се случва "МЕКО"

<!-- 
## Технологичен стек:
- **Java 8+**
- **Spring Boot** (с Spring Web за създаване на RESTful услуги)
- **Maven** (за управление на зависимости)
- **Spring Boot DevTools** (по избор, за по-бързо разработване)

## Структура на проекта:

### Контролери:
- Обработват HTTP заявки, делегират на услуги и връщат отговори.
- Пример: `TaskController.java`

### Услуги:
- Бизнес логика за управление на задачи (CRUD операции в паметта).
- Пример: `TaskService.java`

### Модели:
- Дефинират структурата на една `Task`.
- Пример: `Task.java`

### Обработка на изключения:
- Централизирана обработка на грешки за ресурс не е намерен, невалиден вход и др.
- Пример: `GlobalExceptionHandler.java`

---

## Example Scenarios:

#### Създаване на нова задача:
**Request:**
```json
POST /tasks
{
  "title": "Complete assignment",
  "description": "Finish the math assignment",
  "status": "PENDING",
  "dueDate": "2024-10-31"
}
```

**Response**
```json
{
  "id": 1,
  "title": "Complete assignment",
  "description": "Finish the math assignment",
  "status": "PENDING",
  "dueDate": "2024-10-31"
}
```

####  Взимане на всички задачи:

**Request:**

GET /tasks

**Response:**
```json
[
  {
    "id": 1,
    "title": "Complete assignment",
    "description": "Finish the math assignment",
    "status": "PENDING",
    "dueDate": "2024-10-31"
  }
]
```

#### Update a Task’s Status:

**Request:**

PUT /tasks/1
```json
{
  "status": "IN_PROGRESS"
}
```

**Response:**
```json
{
  "id": 1,
  "title": "Complete assignment",
  "description": "Finish the math assignment",
  "status": "IN_PROGRESS",
  "dueDate": "2024-10-31"
}
```

#### Delete a Task:


**Request:**
DELETE /tasks/1

**Response:**
204 No Content -->
