# GraphQL - Câmara dos Deputados
GraphQL API with data of the brazilian deputies chamber.

![image](https://user-images.githubusercontent.com/3718366/56861149-31060600-6996-11e9-9f8b-1e6a2b3043e2.png)

# Purpose of the project

The purpose that motivated me to create this project is to make easier for developers to consume this data and create
new apps (mobile, web, etc.) to deliver good information for citizens in Brazil or the world.

# Original REST API doc

https://dadosabertos.camara.leg.br/swagger/api.html

# Demo

[Demo](https://graphql-camara-deputados.herokuapp.com/)

# Install

Install all the dependencies with: `yarn`

# Run dev server

To run the server just run: `yarn start:dev`

# Run production server

To run the production version of the server already transpiled and without the need of `babel-node`, follow these steps.

You just need to run one commend and the transpiled code will be created on `./dist` folder. And run the production code:

```
yarn start
```

If you just want to build the production mode you can just run:

```
yarn build
```

# Some examples of queries

```
# List of deputies
query {
  deputados (first: 20, after: "MQ==") {
    pageInfo {
      endCursor
      hasNextPage
    }
    edges {
      cursor
      node {
        id
        siglaPartido
        urlFoto
      }
    }
  }
}
```

```
# Data from one deputy
query {
  deputado(id: "178912") {
    id
    nomeCivil
    cpf
    dataNascimento
    escolaridade
    municipioNascimento
    ufNascimento
    dataFalecimento
    sexo
    ultimoStatus {
      siglaPartido
      uriPartido
      urlFoto
      gabinete {
        andar
        email
        nome
        predio
        sala
        telefone
      }
    }
  }
}
```

```
# Expenses of a deputy
query {
  deputadoDespesas(id: "178912", after: "MQ==", first: 15) {
    pageInfo {
      endCursor
      hasNextPage
    }
    edges {
      cursor
      node {
        ano
        valorDocumento
        valorLiquido
        cnpjCpfFornecedor
        dataDocumento
        tipoDespesa
        urlDocumento
      }
    }
  }
}
```
