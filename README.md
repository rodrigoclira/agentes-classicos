# Atividade Prática: Agentes Clássicos de Aprendizado por Reforço

**Entrega:** Jupyter Notebook (.ipynb) ou Arquivos python (.py)

**Formato:** Individual

---

## Contexto

Nas aulas, você utilizou Q-Learning e SARSA nos ambientes FrozenLake e CliffWalking. Nesta atividade, você vai aplicar esses algoritmos em um **ambiente diferente**, investigar o efeito dos hiperparâmetros e estender a análise com uma **terceira variante do TD-Learning: o Expected SARSA**.

O código base dos algoritmos (Q-Learning, SARSA e epsilon-greedy) está disponível nos notebooks de aula. 

> [!IMPORTANT]
> **É obrigatório partir desse código**. Adapte-o ao novo ambiente, sem reescrever do zero nem utilizar implementações externas.

---

## Ambiente

Escolha **um** dos ambientes abaixo (todos disponíveis no Gymnasium) ou proponha outro de sua preferência, desde que seja compatível com métodos tabulares (espaço de estados e ações discretos e finitos):                           

- `Taxi-v3` — agente de táxi em grid 5×5; 500 estados, 6 ações
- `Blackjack-v1` — jogo de blackjack contra o dealer; espaço de estados compacto, política ótima conhecida
- `FrozenLake-v1` com mapa 8×8 — versão maior do ambiente já visto

> Justifique brevemente no notebook por que escolheu esse ambiente.

> [!NOTE]
> Caso tenha dúvida na escolha, entre em contato com o professor. 



---

## Tarefas

### Tarefa 1: Exploração do Ambiente (0,5 pt)

- Identifique e descreva: espaço de estados, espaço de ações e estrutura de recompensas
- Execute um agente aleatório por 100 episódios e reporte: taxa de sucesso, recompensa média e número médio de passos
- Inclua ao menos uma visualização do ambiente (render)

---

### Tarefa 2: Expected SARSA (1 pt)

O Expected SARSA é uma variante do SARSA que, em vez de usar o Q-valor da **ação efetivamente tomada** no próximo estado, usa o **valor esperado** considerando a política epsilon-greedy atual.

- **Pesquise** a equação de atualização do Expected SARSA e cite a fonte (livro, artigo ou documentação)
- **Implemente** o algoritmo; você pode usar o código do SARSA fornecido como ponto de partida
- **Explique em 3–5 linhas** no notebook: qual a diferença conceitual entre SARSA e Expected SARSA? Por que isso pode importar na prática?

---

### Tarefa 3: Experimento de Hiperparâmetros (1,0 pt)

Usando **Q-Learning** no ambiente escolhido, investigue o impacto de ao menos **dois hiperparâmetros** (escolha entre α, γ, ε_min ou decay_rate):

- Treine com ao menos 3 valores diferentes para cada hiperparâmetro variado (mantenha os demais fixos)
- Apresente gráficos comparando as curvas de aprendizado (recompensa média por episódio, com janela de suavização)
- Discuta: qual configuração convergiu mais rápido? Qual alcançou o melhor desempenho final?

---

### Tarefa 4: Comparação dos Algoritmos (1,5 pt)

Com os **melhores hiperparâmetros** encontrados na Tarefa 3, treine e avalie os três algoritmos no mesmo ambiente:

- Q-Learning
- SARSA
- Expected SARSA

Apresente:

- Gráfico comparativo das curvas de aprendizado
- Tabela com recompensa média e desvio padrão na fase de avaliação (sem exploração)
- Análise escrita (mínimo 1 parágrafo por algoritmo): o comportamento observado condiz com o esperado pela teoria? Houve diferenças relevantes entre os três?

---

## Critérios de Avaliação

| Critério | Observação |
|---|---|
| Código funcional e organizado | Células com saída visível; sem erros não tratados |
| Correção das implementações | Expected SARSA com equação correta |
| Qualidade dos gráficos | Legendas, títulos e eixos nomeados |
| Profundidade da análise escrita | Vai além de descrever o gráfico — interpreta e relaciona com a teoria |
| Citação da fonte do Expected SARSA | Obrigatória para pontuar a Tarefa 2 |

---

## Dicas

- Comece com poucos episódios para testar se o código está funcionando antes de rodar experimentos longos
- Fixe a seed (`np.random.seed`) para garantir reprodutibilidade
- Se os resultados ficarem muito ruins, reveja os hiperparâmetros — alguns ambientes precisam de mais episódios ou taxas de aprendizado diferentes dos usados em aula
