# Gabarito dos exercícios
A seguir encontra-se uma sugestão de solução para os exercícios propostos.

## Exercícios de fixação

## INNER JOIN
**Exercício 1:** Crie uma *query* utilizando o **INNER JOIN** para retornar duas colunas nomeadas por “Título” e “Língua”, respectivamente, com registros sobre os títulos dos filmes e os nomes de suas línguas. Use as tabelas **film** e **language**.

### Solução
```
SELECT 
    fil.title AS `Título`, lan.name AS `Língua`
FROM
    sakila.film AS fil
        INNER JOIN
    sakila.language AS lan ON fil.film_id = lan.language_id;
```

**Exercício 2:** Crie uma *query* utilizando o **INNER JOIN** para retornar duas colunas nomeadas por “Título” e “Categoria”, respectivamente, com registros sobre os títulos dos filmes e os nomes de suas categorias. Use as tabelas **film_category**, **film** e **category**.

### Solução
```
SELECT 
    fil.title AS `Título`,
    cat.name AS `Categoria`
FROM
    sakila.film_category AS fc
		INNER JOIN
	sakila.film AS fil ON fc.film_id = fil.film_id
		INNER JOIN
	sakila.category AS cat ON fc.category_id = cat.category_id;
```
**Exercício 3:** Gerar três colunas nomeadas por "Loja_Id", "Gerente" e "Email", respectivamente, com registros sobre os *ids* das lojas, os nomes completos dos gerentes e seus *emails*. Use as tabelas **store**, e **staff**.

### Solução
```
SELECT 
    sto.store_id AS `Loja_Id`,
    CONCAT(sta.first_name, ' ', sta.last_name) AS `Gerente`,
    sta.email AS `Email`
FROM
    sakila.store AS sto
        INNER JOIN
    sakila.staff AS sta ON sto.manager_staff_id = sta.staff_id;
```

**Exercício 4:** Gerar três colunas nomeadas por "Cliente_Id", "Cliente", e "Endereço_Loja", respectivamente, com registros sobre os *ids* dos clientes, seus nomes completos e os endereços das loja que são cadastrados. Use as tabelas **customer**, **store** e **address**.

### Solução
```
SELECT 
    cus.customer_id AS `Cliente_Id`,
    CONCAT(cus.first_name, ' ', cus.last_name) AS `Cliente`,
    adr.address AS `Endereço_Loja`
FROM
    sakila.customer AS cus
        INNER JOIN
    sakila.store AS sto ON cus.store_id = sto.store_id
        INNER JOIN
    sakila.address AS adr ON sto.address_id = adr.address_id;
```

**Exercício 5:** Gerar quatro colunas nomeadas por "Alugel_Id", "Filme", "Data_Aluguel" e "Data_Retorno", respectivamente, com registros sobre os *ids* dos aluguéis, os nomes dos filmes alugados e suas datas de aluguéis e devoluções. Use as tabelas **rental**, **inventory** e **film**.

### Solução
```
SELECT 
    ren.rental_id AS `Aluguel_Id`,
    fil.title AS `Filme`,
    ren.rental_date AS `Aluguel_Data`,
    ren.return_date AS `Aluguel_Retorno`
FROM
    sakila.rental AS ren
        INNER JOIN
    sakila.inventory AS inv ON ren.inventory_id = inv.inventory_id
        INNER JOIN
    sakila.film AS fil ON inv.film_id = fil.film_id;
```

## Exercícios

**Exercício 1:** Crie uma query que gere o histórico de aluguéis de filmes utilizando o INNER JOIN para retornar quatro colunas nomeadas por "Aluguel_Id", "Filme", "Cliente" e “Funcionário”. As colunas devem possuir, respectivamente, registros sobre os *ids* dos aluguéis, nomes dos filmes, nome completo dos clientes e funcionários. Utilize as tabelas **rental**, **inventory**, **film**, **staff**: 

### Solução
```
SELECT 
    ren.rental_id AS `Aluguel_Id`,
    fil.title AS `Filme`,
    CONCAT(cus.first_name, ' ', cus.last_name) AS `Cliente`,
    CONCAT(sta.first_name, ' ', sta.last_name) AS `Funcionário`
FROM
    sakila.rental AS ren
        INNER JOIN
    sakila.inventory AS inv ON ren.inventory_id = inv.inventory_id
        INNER JOIN
    sakila.film AS fil ON inv.film_id = fil.film_id
        INNER JOIN
    sakila.customer AS cus ON ren.customer_id = cus.customer_id
        INNER JOIN
    sakila.staff AS sta ON ren.staff_id = sta.staff_id;

```