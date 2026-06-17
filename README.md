# Painel de Planos de Contingência — REDEC Sul I

Painel estático (HTML único) para acompanhar quais municípios da REDEC Sul I
entregaram o Plano de Contingência (PLANCON) atualizado, e quais ainda não.

Fonte dos dados: pasta **PLANCON 2026 → REDEC 5** no Google Drive.
Os dados ficam embutidos no próprio `index.html` — não há conexão automática
ao Drive (por desenho, para manter isso simples e sem custos de hospedagem).

## Como publicar (primeira vez)

1. Crie um repositório novo no GitHub (pode ser público ou privado — se for
   privado, o GitHub Pages exige plano pago, então para 5 colegas o mais
   simples é deixar **público**).
2. Faça upload deste `index.html` e deste `README.md` para o repositório
   (botão **Add file → Upload files**).
3. Vá em **Settings → Pages**.
4. Em "Build and deployment", selecione **Deploy from a branch**, branch
   `main`, pasta `/ (root)`. Salve.
5. Em ~1 minuto o GitHub mostra o link do site (algo como
   `https://seu-usuario.github.io/nome-do-repo/`). Compartilhe esse link com
   os colegas.

## Critério usado para "atualizado"

Um município conta como **atualizado** se tiver pelo menos um documento na pasta
REDEC 5 do ano atual **ou** do ano anterior (ex: em 2026, vale ter algo em
"PLANCON 2025" ou "PLANCON 2026"), já que os planos têm validade de um ano.
Só fica como **não entregue** quem não tem nenhum documento em nenhuma das
duas pastas.

## Como atualizar quando chegam novos PDFs

Este painel **não atualiza por conta própria**. O fluxo é:

1. Peça para o Claude (nesta conversa ou em uma nova, mencionando a pasta do
   Drive) reler a pasta `PLANCON 2026 / REDEC 5` e gerar um novo
   `index.html`.
2. No repositório do GitHub, vá no arquivo `index.html` → ícone de lápis
   (editar) ou **Add file → Upload files** marcando para substituir.
3. Cole/suba o novo conteúdo e clique em **Commit changes**.
4. O site atualiza automaticamente em menos de um minuto — ninguém precisa
   recarregar nada além da própria página.

## Evoluções possíveis (não implementadas agora)

- **Automação real**: uma GitHub Action rodando todo dia, lendo o Drive via
  uma credencial de serviço do Google Cloud, e commitando o `index.html`
  sozinha — sem precisar pedir para o Claude. Isso exige criar um projeto no
  Google Cloud Console e uma service account com acesso de leitura à pasta.
- **Histórico**: guardar versões antigas dos dados para ver a evolução mês a
  mês.
