# Documentação de Testes da API

## Como fazer os testes

```http
POST https://api.exemplo.com/usuarios
Headers:
  Content-Type: application/json
  Authorization: Bearer token123
Body:
{
  "nome": "João",
  "email": "joao@exemplo.com"
}
```

---

## **1. Testes Básicos a Realizar**

1. **Validação de status code**
   - `200 OK`
   - `201 Created`
   - `400 Bad Request`
   - `401 Unauthorized`
   - `404 Not Found`
   - `500 Internal Server Error`
  
2. **Validação do corpo da resposta (Response Body)**
   - Está no formato esperado? (JSON, XML)
   - Contém os campos corretos?
  
3. **Validação dos headers**
   - Verificar `Content-Type`, `Authorization`, etc.
  
5. **Testes negativos**
   - O que acontece com dados inválidos?
   - Falta de autorização?
   - Campos obrigatórios ausentes?
  
6. **Testes de limites**
   - Campos com tamanho máximo
   - Número máximo de registros (ex: paginação)

---

## **2. Checklist de Teste Manual**

<h2>Checklist de Teste Manual</h2>
<form id="checklist">
  <label><input type="checkbox"> Teste com dados válidos (happy path)</label><br>
  <label><input type="checkbox"> Teste com dados inválidos</label><br>
  <label><input type="checkbox"> Campos obrigatórios ausentes</label><br>
  <label><input type="checkbox"> Teste de autenticação/autorização</label><br>
  <label><input type="checkbox"> Teste de performance básica (tempo de resposta)</label><br>
  <label><input type="checkbox"> Teste com diferentes usuários (perfis)</label><br>
</form>

---

## **3. Exemplo de Caso de Teste**

| Item                | Descrição                                                                  |
|---------------------|----------------------------------------------------------------------------|
| **ID**              | TC001                                                                      |
| **Objetivo**        | Criar usuário com dados válidos                                            |
| **Método**          | POST                                                                       |
| **Endpoint**        | `/usuarios`                                                                |
| **Headers**         | `Authorization: Bearer token`, `Content-Type: application/json`            |
| **Body**            | `{ "nome": "Maria", "email": "maria@ex.com" }`                             |
| **Esperado**        | Status 201, campo `"id"` no body                                           |
| **Resultado Obtido**| (preencher após teste)                                                     |
| **Status**          | Aprovado / Reprovado                                                       |

---

## **Exemplo de BDD**

Cenário: Criar usuário com dados válidos

```gherkin
Funcionalidade: Cadastro de usuários

  Cenário: Criar usuário com dados válidos
    Dado que tenho acesso à API com token de autorização válido
    E possuo os seguintes dados no corpo da requisição:
      | nome  | email         |
      | Maria | maria@ex.com  |
    Quando envio uma requisição POST para o endpoint "/usuarios"
    Então a resposta deve conter o status 201
    E o corpo da resposta deve conter o campo "id" não nulo

```
