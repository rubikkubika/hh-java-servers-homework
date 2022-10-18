## Домашнее задание - Servlet API, Jetty, Jersey

Задача - написать два приложения, которые слушают порт 8081. В качестве контейнера сервлетов используем Jetty

## Первое приложение

Использует только сервлеты. Нужно написать приложение-счетчик – хранить в памяти состояние, 
которое изменяется через HTTP походы. Используйте подходящие коды HTTP ответов из лекции по HTTP


`GET: /counter` - возвращает счетчик

`POST: /counter` - увеличивает счетчик на 1

`DELETE: /counter` - уменьшает счетчик на значение, которое передается в заголовке «Subtraction-Value»

`POST: /counter/clear` - сбрасывает счетчик. 
Для выполнения этого запроса должна быть cookie - «hh-auth», единственное условие - она должна быть длиннее 10 символов. 


## Второе приложение

Использует Jersey и JAX-RS аннотации, в т.ч для чтения cookie и заголовков.

Делает то же самое, что приложение 1, изменен только формат ответа для запроса `GET: /counter`:
```json
{
    "date": "текущая дата-время в формате ISO",
    "value": "значение счетчика"
}
```
Для сериализации должен использоваться Jackson

В лекции в примере с Jersey для конфигурирования ресурсов мы использовали способ не из стандарта jax-rs
(мы использовали параметр `jersey.config.server.provider.packages`)
В домашке jersey-приложение **должно использовать класс javax.ws.rs.core.Application**

---
Оба приложения сейчас можно запустить через `mvn exec:java` из папки подпроекта (или из IDE, как удобнее)