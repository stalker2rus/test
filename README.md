# Инструкция по работе с Postman коллекцией.

В моей колекции уже есть токен, но вот инструкции как получять токен API GitHub:
1. Для того чтобы получить токен, необходимо иметь аккаунт в GitHub 
2. Необходимо нажать на иконку профиля зайти в "Settings"
3. Перейти в "Developer settings" 
4. Далее "Personal access tokens" и выбрать "Tokens (classic)"
5. Далее "Generatу new token"
6. Далее ввести название токена, выбрать срок действи и разрешения после нажать "Generate token"
Токен хранится в переменной коллекции "token".
<br>
У коллекции есть переменные (Variables): <br>
"baseURL" - адрес на который делать API запросы<br>
"user" - имя пользователя GitHub<br>
"repo" - имя репозитория пользователя в GitHub<br>
"i.numb" - номер созданного issue для передачи между запросами<br>
<br>
<a href="https://github.com/stalker2rus/test/blob/main/GitHub.postman_collection.json")>Ссылка</a> на Postman коллекцию
<br> 
<br> 
В коллекция "GitHub" 4 запроса:
<br>
1. POST “Create issue 1” - cоздаёт issue с названием Issue 1, описанием Something went wrong. label — bug — и assignee — (текущий логин на GitHub). Всё это указывается в body в формате JSON.    <br> 
В tests добавлены проверки что:  <br> 
- Статус код 201<br> 
- В теле ответа содержится id issue, это означает что оно точно создалось <br> 
- В переменную "i_nub" записывается номер issue, для выполнения дальнейщих запросов  <br>
<br> 
2. GET "Get list issues" - выводит список все issues. <br>
В tests добавлены проверки что:<br> 
 - Статус код 200<br> 
<br> 
<br> 
3. PATCH “Rename issue 1 to issie 2” - изменяет название созданной задачи на "Issue 2".<br>    
В tests добавлены проверки что:<br> 
 - Статус код 200<br> 
 - В теле ответа содержится id issue, это означает что оно точно создалось<br> 
<br> 
<br>  
4. DELETE “Lock issie 2” - в задании было сказано "Удалите Issue 2", но GitHub не поддерживает удалене Issue по API хотя и есть метод DELETE, в место этого этот метотд делаеть разблокировку issie для редактирования.<br>    
В tests добавлены проверки что:<br> 
 - Статус код 204<br> 
