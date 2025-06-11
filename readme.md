# ☕🚀 Java 21 com AWS Lambda – Cold Start Otimizado

Este projeto demonstra o uso de **Java 21** em uma função **AWS Lambda** com foco em **baixa latência de cold start**, ideal para aplicações que demandam alta disponibilidade e resposta rápida mesmo após períodos de inatividade.

---

## 🌐 Endpoint de Demonstração

🔗 URL pública:
```
https://ws6djesz37.execute-api.us-east-1.amazonaws.com/develop/greetings/teste
```

📥 **Resposta esperada**:
```json
{
  "id": 1,
  "content": "Hello, teste!"
}
```

> O campo `id` é um contador simples.  
> Sempre que a Lambda estiver fria (cold start), o `id` volta para `1`.  
> Assim, é possível **monitorar os cold starts** diretamente pelo valor do `id`.

---

## 🔍 Destaques Técnicos

- ✅ **Java 21 (LTS)**: com avanços significativos em desempenho.
- 🧊 **Baixo Cold Start**: inicialização otimizada via GraalVM nativa ou melhorias na JDK 21.
- 🛠️ **AWS Lambda**: integrada ao API Gateway para fácil consumo HTTP.
- 📈 **Observabilidade**: contador interno para detecção de cold starts.

---

## 🚀 Como testar o cold start?

1. Acesse a URL acima várias vezes em sequência — o `id` será incrementado.
2. Aguarde alguns minutos de inatividade (geralmente 5 a 15 minutos).
3. Acesse novamente e observe se o `id` reinicia para `1` — isso indica que a função estava fria.

---

## 🧪 Como compilar e fazer deploy

### 🔨 Build da função
```shell
sam build --use-container
```

### 🚀 Deploy da função
```shell
sam deploy --guided --profile api-dev
```

---

## 📦 Tecnologias Utilizadas

- Java 21 ☕
- AWS Lambda 🟡
- AWS API Gateway 🌐
- Maven ou Gradle 🧱
- Amazon Corretto ou GraalVM 🔥
- AWS SAM CLI 📦

---

## 📁 Estrutura do Projeto

```
├── HELP.md
├── mvnw
├── mvnw.cmd
├── pom.xml
├── readme.md
├── samconfig.toml
├── src
│   ├── main
│   │   ├── java
│   │   │   └── br
│   │   │       └── com
│   │   │           └── likwi
│   │   │               └── snapstart
│   │   │                   ├── GreetingController.java
│   │   │                   ├── Greeting.java
│   │   │                   ├── LambdaHandler.java
│   │   │                   └── SnapstartApplication.java
│   │   └── resources
│   │       ├── application.properties
│   │       ├── static
│   │       └── templates
│   └── test
│       └── java
│           └── br
│               └── com
│                   └── likwi
│                       └── snapstart
│                           └── SnapstartApplicationTests.java
└── template.yaml
```

---

## 📚 Sobre Cold Start

Em funções Lambda, o "cold start" acontece quando:

- A função fica inativa por um tempo.
- Uma nova instância precisa ser criada para lidar com a requisição.

Usar Java em funções Lambda tradicionalmente trazia tempos maiores de inicialização. Com **Java 21** e boas práticas, é possível reduzir esse tempo significativamente.

---

## 🧠 Dica Dev

Para reduzir ainda mais o cold start:

- Use **SnapStart** (quando disponível).
- Reduza o número de dependências.
- Evite inicialização pesada no construtor.
- Considere usar **graalVM native-image** em cenários extremos.

---

## 📫 Feedback

Se você testou esse exemplo ou quer contribuir com sugestões, abra um PR ou envie um issue!

---
