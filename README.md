# Agenda Expogenética 2026 — Ponta

App de agenda da equipe na feira: presença por dia, eventos com responsáveis, cobertura do estande, exportação em Excel e PNG da agenda individual.

A agenda inteira vive num único arquivo: `dados/agenda.json`. O app lê e grava esse arquivo direto no GitHub, então todo mundo enxerga a mesma versão.

---

## 1. Criar o repositório

1. No GitHub, **New repository**.
2. Nome sugerido: `agenda-expogenetica`.
3. Marque **Public** (assim quem só vai *consultar* não precisa de nada).
   - Se preferir **Private**, funciona igual, mas aí *até para ler* cada pessoa vai precisar de um token.
4. Suba estes arquivos, mantendo a estrutura:

```
index.html
dados/agenda.json
README.md
```

## 2. Ligar o GitHub Pages

1. Repositório → **Settings** → **Pages**.
2. Em *Build and deployment*, **Source: Deploy from a branch**.
3. Branch: `main`, pasta `/ (root)` → **Save**.
4. Em um ou dois minutos o endereço aparece ali, no formato:

```
https://SEU-USUARIO.github.io/agenda-expogenetica/
```

Esse é o link para mandar para a equipe.

## 3. Quem só consulta

Abre o link e pronto. O app descobre o repositório pela própria URL e carrega `dados/agenda.json` sozinho. Dá para navegar, exportar a planilha e baixar o PNG da agenda. As alterações que essa pessoa fizer ficam só no navegador dela.

## 4. Quem edita e publica

Precisa de um token pessoal do GitHub, uma vez só:

1. GitHub → foto do perfil → **Settings** → **Developer settings** → **Personal access tokens** → **Fine-grained tokens** → **Generate new token**.
2. **Repository access**: *Only select repositories* → escolha `agenda-expogenetica`.
3. **Permissions** → *Repository permissions* → **Contents: Read and write**. Só isso.
4. Defina a validade (ex.: até setembro/2026) e gere. **Copie o token na hora** — ele não aparece de novo.
5. No app, botão **Compartilhar (GitHub)**, cole o token no campo indicado e clique em **Fechar**.

A partir daí:

- **Buscar do GitHub** — traz a versão mais recente de lá.
- **Enviar para o GitHub** — publica a sua versão para todo mundo.

O selo no topo mostra `sincronizado` ou `alterações não enviadas`.

> O token fica guardado apenas no navegador de quem colou. Ele **não** entra no `agenda.json`, nem no backup em JSON, nem no repositório. O botão **Esquecer token** apaga do navegador.

## 5. Como evitar atropelo entre duas pessoas

O arquivo é gravado inteiro a cada envio, então vale a regra: **clique em "Buscar do GitHub" antes de começar a mexer**.

Se alguém publicou algo depois que você carregou, o app avisa na hora do envio e deixa você escolher entre sobrescrever ou parar e buscar a versão de lá primeiro. Nada é gravado sem essa confirmação.

Como cada envio é um commit, o histórico do arquivo fica em
`https://github.com/SEU-USUARIO/agenda-expogenetica/commits/main/dados/agenda.json`
e dá para voltar qualquer versão antiga por ali.

## 6. Backup

Independente do GitHub, os botões **Salvar backup** e **Abrir backup** exportam e importam a agenda como JSON. Serve para levar de um navegador para outro sem token.

---

## Estrutura

| Arquivo | O que é |
|---|---|
| `index.html` | O app inteiro: sem build, sem dependências, sem servidor |
| `dados/agenda.json` | Os dados: pessoas, dias, presença, eventos, saídas do estande e contatos |
