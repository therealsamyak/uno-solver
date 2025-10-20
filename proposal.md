# Title:
2-Player UNO Solver

## Summary:
We develop an optimal game-theoretic solver for 2-player UNO by formulating it as a POMDP and applying reinforcement learning techniques (Q-learning, policy gradient methods) to learn near-optimal strategies, addressing the challenge of solving large imperfect-information games with complex action spaces and stochastic elements.

## Splash images
*[Placeholder for game state visualization showing observable vs hidden information in UNO]*

*[Placeholder for learning curves comparing RL algorithms and win rates vs baseline strategies]*

## Project git repo(s):
https://github.com/therealsamyak/uno-solver

---

## Big picture 

### What is the overall problem that this and related research is trying to solve?
The broader research goal is to develop scalable algorithms for solving sequential decision-making problems under uncertainty, particularly in adversarial multi-agent environments. This encompasses finding optimal or near-optimal strategies in partially observable settings where agents must reason about hidden state and opponent behavior.

### Why should people (everyone) care about the problem?
Games with imperfect information mirror real-world decision-making scenarios where agents must act under uncertainty—from competitive strategy and negotiations to cybersecurity, financial trading, and resource allocation. Advances in solving these problems have direct applications in multi-agent systems, automated negotiation, adversarial planning, and understanding strategic behavior in competitive environments where information asymmetry is fundamental.

### What has been done so far to address this problem?
Deep reinforcement learning has achieved superhuman performance in perfect-information games (AlphaGo, chess), while methods combining RL with game-theoretic reasoning have succeeded in poker (Pluribus). Traditional approaches include minimax search with alpha-beta pruning for perfect information, and POMDP solvers for single-agent uncertainty. However, most multi-agent RL work focuses on cooperative settings or simple competitive games, leaving complex adversarial card games with rich rule systems relatively unexplored.

---

## Specific project scope

### What subset of the overall big picture problem are you addressing in particular?
We focus on solving 2-player UNO, formulated as a two-agent competitive POMDP. UNO features partial observability (hidden opponent hands), stochastic transitions (card draws), and a highly structured action space with special cards (Skip, Reverse, Draw Two, Wild, etc.). This represents a distinct challenge due to asymmetric information, variable hand sizes, and rule-based action constraints.

### How does solving this subproblem lead towards solving the big picture problem?
UNO introduces complexities that stress-test multi-agent RL algorithms: partial observability requiring opponent modeling, stochastic state transitions, large discrete action spaces with legality constraints, and non-stationary opponent policies during learning. Successfully solving UNO demonstrates that RL methods can handle adversarial card games beyond poker's betting-focused structure, expanding the frontier of tractable multi-agent sequential decision problems.

### What is your specific approach to solving this subproblem?
We formulate 2-player UNO as a competitive POMDP where each player's state includes their hand, the visible upcard, and beliefs about opponent hands. We implement and compare multiple RL approaches:
1. **Q-learning** with function approximation using neural networks to handle large state spaces
2. **Policy gradient methods** (REINFORCE, actor-critic) to directly optimize strategy
3. **Self-play training** where agents improve by playing against copies of themselves, inspired by AlphaGo's approach

### How can you be reasonably sure this approach will result in a solution?
Deep RL has proven successful in games of similar or greater complexity (Dota 2, StarCraft). UNO's finite game length and clear reward signal (win/loss) provide stable learning objectives. We employ established techniques: function approximation for generalization, epsilon-greedy exploration for state-space coverage, and self-play for robust strategy development. Convergence is validated through performance against baselines and strategy stability metrics.

### How will we know that this subproblem has been satisfactorily solved, using quantitative metrics?
Success metrics include:
1. **Win rate** against baseline strategies (random play ≥95%, rule-based heuristics ≥80%, human-level play ≥60%)
2. **Learning curves** showing consistent improvement and convergence within 10^5 training games
3. **Cross-evaluation** with trained agents beating each other ~50% of the time (indicating converged strategies)
4. **Ablation studies** quantifying the value of different card types and strategic decisions

---

## Broader impact

### What is the value of your approach beyond this specific solution?
Our implementation provides an open-source framework for applying RL to turn-based card games with partial observability. The POMDP formulation, state representation, and opponent modeling techniques we develop are transferable to other shedding-type card games (Crazy Eights, Mau-Mau), trick-taking games, and board games with hidden information. The function approximation architecture and training methodology can inform solver design for similar multi-agent problems.

### What is the value of this solution beyond solely solving this subproblem and getting us closer to solving the big picture problem?
A trained UNO agent provides a testbed for human-AI interaction research, studying how humans learn and adapt to optimal strategies in familiar games. It enables analysis of strategic misconceptions in casual play and serves as an educational tool for teaching POMDP formulation and RL in game theory courses. Additionally, UNO's popularity makes the solver accessible for public engagement with AI concepts, demonstrating reinforcement learning to broader audiences through an intuitive domain.

---

## Background / related work / references
See [literature review](literature_review.md) for comprehensive survey of POMDP solution methods, multi-agent reinforcement learning, game-playing AI, and related work on card game agents.

---

## System capabilities, validation deliverables, engineering tasks

### Concrete external deadlines (paper submissions):
- **Target:** IEEE Conference on Games (CoG) 2026 (Submission: April 2026)
  - **Proposed title:** "Learning to Play UNO: A Reinforcement Learning Approach to Adversarial Card Games with Partial Observability"
  - **Abstract:** Formulates 2-player UNO as a competitive POMDP, compares RL algorithms (Q-learning, policy gradients, self-play), reports win rates against baselines, and analyzes emergent strategic behaviors

### Detailed schedule (weekly capabilities / deliverables / tasks):
See [project schedule](schedule.md) for week-by-week breakdown of implementation milestones, validation checkpoints, and experimental evaluations.
