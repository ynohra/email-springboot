# Service Email- Spring Boot

![Java](https://img.shields.io/badge/Java-21+-orange)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-4.x-brightgreen)
![Maven](https://img.shields.io/badge/Maven-Build-blue)
![Status](https://img.shields.io/badge/Status-Em%20Desenvolvimento-success)

---

## Sobre o Projeto

Esta aplicação é uma **API REST desenvolvida com Spring Boot** responsável pelo envio de e-mails através da integração com um servidor SMTP.

O projeto foi criado com foco em:

- ✔ Praticar arquitetura em camadas
- ✔ Integrar serviços externos (SMTP)
- ✔ Trabalhar com configuração externa segura
- ✔ Simular um microserviço de notificação
- ✔ Aplicar boas práticas no backend

A API recebe os dados do e-mail via requisição HTTP e realiza o envio utilizando o **Spring Mail**.

---

## Arquitetura

A aplicação segue o padrão de separação de responsabilidades:

### 🔹 Controller 

Responsável por expor o endpoint REST:
```

POST /email

```
Recebe os dados via JSON e delega o envio ao Service.

### 🔹 Service 
Contém a regra de negócio de envio.

Utiliza `JavaMailSender` para montar e disparar a mensagem via SMTP.

### 🔹 Model

Foi utilizado um **record do Java** para representar o objeto Email:

- `to`
- `subject`
- `body`

A escolha do `record` proporciona:

- Imutabilidade
- Código mais enxuto
- Clareza na representação dos dados

---

### Tecnologias Utilizadas


- Java 21+

- Spring Boot

- Spring Web

- Spring Mail

- Maven

- Mailtrap (SMTP para testes)

- Postman (testes de requisições HTTP)
  

### Integração SMTP (Mailtrap)

Durante o desenvolvimento foi utilizado o Mailtrap, um servidor SMTP voltado para testes.

Isso permite:

- Capturar e-mails sem enviá-los para destinatários reais

- Visualizar o conteúdo da mensagem

- Validar a integração com serviço externo
  

As credenciais são configuradas no arquivo:

```
application.properties
```

Exemplo:

```
spring.mail.host=sandbox.smtp.mailtrap.io
spring.mail.port=587
spring.mail.username=SEU_USERNAME
spring.mail.password=SEU_PASSWORD
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true
```

▶️ Como Executar o Projeto

1️⃣ Clonar o repositório

```
git clone https://github.com/seu-usuario/email-springboot.git
```

2️⃣ Acessar a pasta do projeto

```
cd email-springboot
```

3️⃣ Buildar o projeto
```
./mvnw clean package
```

Ou no Windows:
```
mvnw.cmd clean package
```

4️⃣ Executar a aplicação
```
java -jar target/email-springboot-0.0.1-SNAPSHOT.jar
```

A aplicação iniciará em:
```
http://localhost:8080
```
---

### Testando a API
Os testes foram realizados utilizando o Postman.

Endpoint
```
POST http://localhost:8080/email
```

Body (JSON)
```
{
  "to": "teste@email.com",
  "subject": "Teste Spring Boot",
  "body": "Funcionando 🚀"
}
```

Após a requisição:

**1.** A API recebe os dados

**2.** O Controller delega para o Service

**3.** O Service monta a mensagem

**4.** O Spring envia via SMTP

**5.** O Mailtrap captura o e-mail

---

### Conceitos Demonstrados

✔ Injeção de Dependência

✔ Configuração via application.properties

✔ Integração com serviço externo (SMTP)

✔ API REST com Spring MVC

✔ Separação em camadas

✔ Uso de Java moderno (record)

✔ Teste manual de API

---

### Autora
Yasmin Nohra
Estudante de Engenharia de Software
Foco em Desenvolvimento Backend com Java

Este projeto faz parte da minha jornada de aprofundamento em backend e integração com serviços externos, evoluindo para arquiteturas mais robustas e microsserviços.
