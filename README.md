# Nexora Software Factory — pacote para Claude Code

Este pacote implementa o framework "Nexora Software Factory" como um
ecossistema real de orquestrador + subagentes no **Claude Code**.

## O que tem aqui

```
nexora-software-factory/
├── CLAUDE.md                  ← instruções do Orquestrador Master
└── .claude/agents/
    ├── produto.md
    ├── arquitetura.md
    ├── ux-ui.md
    ├── frontend.md
    ├── backend.md
    ├── banco-dados.md
    ├── devops.md
    ├── seguranca.md
    ├── ia.md
    ├── qualidade.md
    └── documentacao.md
```

## Como instalar

1. Copie a pasta `nexora-software-factory` para dentro do repositório do
   seu projeto (ou use-a como o próprio repositório, se for começar do zero).
2. Abra o Claude Code dentro dessa pasta. Ele carrega automaticamente o
   `CLAUDE.md` como instruções do orquestrador e reconhece os arquivos em
   `.claude/agents/` como subagentes disponíveis.
3. Descreva sua ideia normalmente (ex: "quero um app de gestão de estoque
   para o meu laboratório"). O orquestrador vai analisar, escolher os
   departamentos certos e delegar.

## Como estender

- **Novo departamento** (ex: Marketing, Financeiro, Dados/BI): crie um novo
  arquivo `.claude/agents/<nome>.md` seguindo o mesmo padrão de frontmatter
  (name, description, tools, model) + instruções. Depois, adicione uma
  linha na tabela de "Departamentos disponíveis" do `CLAUDE.md`.
- **Acionar um departamento manualmente**: peça explicitamente, ex. "use o
  subagente `seguranca` para revisar este endpoint de login".
- **Ajustar rigor**: se algum gate for burocracia demais para um projeto
  pequeno, você pode pedir ao orquestrador para pular uma etapa — ele vai
  avisar o risco e pedir confirmação antes.

## Observações importantes

- Isto roda no **Claude Code** (terminal, VS Code/JetBrains, ou o app
  desktop) — não no claude.ai comum, que não tem orquestração automática
  entre especialistas.
- Os subagentes têm contexto isolado entre si — cada um só vê o que o
  orquestrador passa para ele. Isso é intencional (evita poluir o contexto),
  mas significa que decisões importantes devem estar registradas no
  `CLAUDE.md` ou em arquivos do projeto (ex: um `docs/decisoes.md`) para
  que todos os departamentos as enxerguem.
- Os campos `tools` de cada subagente já seguem o princípio de menor
  privilégio (ex: `qa` não tem acesso a infraestrutura). Ajuste conforme a
  necessidade real do seu projeto.
