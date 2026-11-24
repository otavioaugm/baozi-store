# Baozi Store – API REST

Trabalho da disciplina **Desenvolvimento Web Back-End** (Uninter – ADS).
Aluno: Otavio Costa – RU 3906573

API REST simples para a Baozi Store, uma loja de pão chinês, com cadastro de **clientes**, **produtos** e **pedidos**.

## Tecnologias
- Java 17+
- Spring Boot 3 (Spring Web, MVC)
- Spring Data JPA / Hibernate
- Banco relacional H2 (gravado em arquivo); configuração para MySQL pronta no `application.properties`
- Postman (coleção em `BaoziStore.postman_collection.json`)

## Estrutura (MVC)
```
src/main/java/br/com/baozistore
├── BaoziStoreApplication.java
├── model/        Cliente, Produto, Pedido (entidades JPA)
├── repository/   ClienteRepository, ProdutoRepository, PedidoRepository
├── controller/   ClienteController, ProdutoController, PedidoController
└── dto/          PedidoRequest (JSON de entrada do pedido)
```

## Entidades
| Entidade | Campos |
|---|---|
| Cliente | id (Long), nome (String), clienteDesde (LocalDate) |
| Produto | id (Long), nome (String), preco (BigDecimal), estoque (Boolean) |
| Pedido | id (Long), clienteId (Long → cliente), produtoId (Long → produto), quantidade (Integer) |

## Endpoints
| Método | Rota | Descrição |
|---|---|---|
| POST | /clientes | Cadastra cliente |
| GET | /clientes | Lista clientes |
| GET | /clientes/{id} | Consulta cliente por ID |
| PUT | /clientes/{id} | Atualiza cliente (opcional) |
| DELETE | /clientes/{id} | Apaga cliente |
| POST | /produtos | Cadastra produto |
| GET | /produtos | Lista produtos |
| GET | /produtos/{id} | Consulta produto por ID |
| PUT | /produtos/{id} | Atualiza produto (opcional) |
| DELETE | /produtos/{id} | Apaga produto |
| POST | /pedidos | Registra pedido |
| GET | /pedidos | Lista pedidos |
| GET | /pedidos/{id} | Consulta pedido por ID |
| PUT | /pedidos/{id} | Atualiza pedido (opcional) |
| DELETE | /pedidos/{id} | Apaga pedido |

Exemplo de JSON para registrar pedido:
```json
{ "clienteId": 1, "produtoId": 1, "quantidade": 6 }
```

## Como executar
1. Instale o JDK 17 ou superior e, no VS Code, a extensão **Extension Pack for Java**.
2. Abra esta pasta no VS Code e aguarde o download das dependências do Maven.
3. Abra `BaoziStoreApplication.java` e clique em **Run** acima do método `main`.
4. A API sobe em `http://localhost:8080`. O console do banco fica em `http://localhost:8080/h2-console`
   (JDBC URL `jdbc:h2:file:./data/baozistore`, usuário `sa`, senha em branco).
