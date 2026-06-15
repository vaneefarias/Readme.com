# Descobrindo Notebook LLM's #projetoDIO

# Busca Gulosa de Melhor Escolha (Greedy Best-First Search)

A **busca gulosa de melhor escolha** (*Greedy Best-First Search*) é uma estratégia de busca informada que tenta expandir o nó que parece estar mais próximo do objetivo. Ela utiliza apenas uma função heurística, denotada por $h(n)$, para avaliar os nós, ou seja:

$$f(n) = h(n)$$

A função $h(n)$ representa o custo estimado do caminho de menor custo entre o estado do nó $n$ e um estado objetivo.

Este algoritmo é frequentemente chamado de **"ambicioso"** ou **"ganancioso"** porque, em cada passo, ele tenta alcançar o objetivo o mais rápido possível, sem considerar o custo total do caminho percorrido até aquele momento.

---

## 🗺️ Funcionamento e Exemplo Prático

Um exemplo clássico de busca gulosa (extraído da literatura de *Russell & Norvig*) é o problema de encontrar uma rota entre cidades em um mapa, como o trajeto de **Arad** para **Bucareste**:

1. **A Heurística:** O algoritmo utiliza a *Heurística de Distância em Linha Reta* ($h_{DLR}$), que estima a distância física direta (geométrica) de cada cidade até o objetivo final (Bucareste).
2. **Primeiro Passo:** A partir de *Arad*, o algoritmo avalia os vizinhos e expande *Sibiu*, porque ela é geograficamente mais próxima de Bucareste do que *Zerind* ou *Timisoara*.
3. **Segundo Passo:** Em seguida, ele expande *Fagaras* (a mais próxima de Bucareste entre os sucessores de Sibiu), que por sua vez gera o estado objetivo *Bucareste*.

---

## ⚠️ Limitações da Busca Gulosa

Apesar de sua velocidade e eficiência em cenários específicos, a busca gulosa possui limitações severas:

* **Não é Ótima:** Ela **não garante** o caminho mais curto. No exemplo da Romênia, a rota encontrada via *Sibiu* e *Fagaras* é **32 quilômetros mais longa** do que o caminho ótimo (que seria através de *Rimnicu Vilcea* e *Pitesti*).
* **Incompleta:** O algoritmo pode entrar em laços (loops) infinitos. Por exemplo, ao tentar ir de *Iasi* para *Fagaras*, a heurística pode levar o agente a um beco sem saída (*Neamt*) que o força a voltar para *Iasi*, repetindo o ciclo indefinidamente caso seja uma busca em árvore pura.
* **Complexidade:** No pior caso, a complexidade de tempo e de espaço para a versão em árvore é $O(b^m)$, onde $b$ é o fator de ramificação e $m$ é a profundidade máxima do espaço de busca. No entanto, uma boa função heurística pode reduzir essa complexidade de forma significativa na prática.
