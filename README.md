# Bookd

> Registro de leituras **offline-first**, métricas ricas e rede social minimalista para leitores.  
> Este repositório contém, por enquanto, a documentação de engenharia em LaTeX.

## 📌 Visão Geral
O **Bookd** é um aplicativo Android (Play Store) para registrar leituras (livros, artigos, ensaios, etc.), produzir anotações, acompanhar metas e métricas, e compartilhar publicações/resenhas com outros leitores. O app é **offline-first**: todo cadastro/consulta/edição funciona sem internet e a sincronização ocorre de forma eventual e resiliente.

## 🎯 Objetivos
- **Simplicidade e velocidade**: estética web anos 2000, interface limpa e direta.
- **Offline por padrão**: uso pleno sem rede, com sincronização incremental e resolução de conflitos.
- **Métricas e retrospectivas**: visão mensal/anual, fatias por língua, tags, editoras, autores, formato, período histórico e mapa mundial.
- **Recomendações sérias**: qualidade por IA (ensemble), com explicabilidade e rigor (ex.: h-index/citações para artigos).
- **Rede social nativa**: posts de texto/fotos/vídeos, reviews e controle fino de privacidade.

## 🧱 Subsistemas (alto nível)
1. **Núcleo Offline & Sync** — armazenamento local, fila de mudanças, jobs de sincronização, resolução de conflitos.
2. **Catálogo & Metadados** — obras (Work), versões por ISBN, metadados por DOI, importação/consulta a provedores.
3. **Leituras & Anotações** — leituras, progresso, notas, anexos.
4. **Tags & Metas** — tags pessoais e sugeridas (top 7 do livro), metas anuais/semestre (livros, páginas, streak, por tag).
5. **Social & Publicações** — posts, mídia, amizades, moderação.
6. **Métricas & Retrospectivas** — snapshots, fatias e timeline (por ano de publicação original).
7. **Recomendação & Analytics** — recomendações explicáveis, razões e sinais.
8. **Admin & Governança** — provedores, políticas e auditoria.

## 📂 Estrutura do Repositório (inicial)
```
.
├─ docs/
│  └─ Bookd - Engenharia de Documentos.pdf   # Projeto LaTeX com especificação (requisitos, casos de uso, classes, dicionário)
└─ README.md
```
> Observação: ao longo do projeto, novas pastas serão criadas (`android/`, `backend/`, `infra/`, etc.).

## ✅ Requisitos (resumo)
- **Funcionais (exemplos):**
  - Registrar leituras de qualquer tipo (livro/artigo/ensaio/outros).
  - Importar metadados por ISBN/DOI; fallback para criação manual.
  - Upload de anotações como texto e/ou anexos (sem limite de caracteres).
  - Metas anuais/semestre (livros, páginas, streak, por tag).
  - Rede social: amigos, posts, reviews com foto/vídeo, controle de visibilidade.
  - Retrospectivas mensais/anuais estilo “Spotify Wrapped”.
- **Não Funcionais (exemplos):**
  - Offline-first com sincronização eventual e incremental.
  - Desempenho local (offline) ≤ 150ms para ações comuns.
  - Acessibilidade AA, leitores de tela, fontes escaláveis.
  - Segurança: TLS em trânsito; opção de criptografia local de notas.
  - Portabilidade: Android 8.0+; provedores plugáveis de metadados.

## 🛠️ Stack (proposta)
- **Mobile**: Android (Kotlin), Room/SQLDelight, WorkManager (jobs), Jetpack Compose (UI minimalista).
- **Sync/API**: REST/GraphQL; back-end (a definir) com endpoints idempotentes e versões por entidade.
- **Recomendações**: pipeline híbrido (CF + conteúdo + rigor), storage de sinais e versões dos modelos.
- **Mídia**: armazenamento externo com upload resiliente/retomável.
- **Infra**: observabilidade, auditoria e políticas de provedores (ISBN/DOI/mídia).

## 🗺️ Roadmap (alto nível)
1. **MVP offline**: leituras, notas, tags pessoais, metas simples; sync básico.
2. **Catálogo/Import**: ISBN/DOI e versões por edição.
3. **Métricas**: snapshots mensais/anuais e retrospectivas.
4. **Social**: posts/reviews e amizades.
5. **Recomendações**: conjunto inicial + explicabilidade.
6. **Polimento**: acessibilidade, testes, segurança e Play Store.

## 🧪 Como contribuir
- Abra issues descrevendo claramente o problema/feature.
- Pull requests com escopo pequeno e testes (quando aplicável).
- Padrão de mensagens de commit: `tipo(escopo): resumo` (ex.: `feat(sync): fila de LocalChange`).

## 🔒 Licença
Definir (ex.: MIT/Apache-2.0).

## 📮 Contato
- Autor/Coordenação: (preencher)
- Issue tracker: via GitHub Issues

---
**Dica rápida:** ao editar o LaTeX, para linhas que estouram coluna, use `\allowbreak{}` nos pontos naturais (depois de vírgula/underline ou entre partes do identificador).
