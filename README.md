<h1>ExpNo 9: Solve Wumpus World Problem using Python demonstrating Inferences from Propositional Logic</h1> 
<h3>Name:        SHIVASRI               </h3>
<h3>Register Number/Staff Id:   212224220098             </h3>
<H3>Aim:</H3>
<p>
    To solve  Wumpus World Problem using Python demonstrating Inferences from Propositional Logic
</p>
<h1>Problem Description</h1>
<hr>
<h2>Wumpus World</h2>
<hr>
The Wumpus world is a simple world example to illustrate the worth of a knowledge-based agent and to represent knowledge representation.

The figure below shows a Wumpus world containing one pit and one Wumpus. There is an agent in room [1,1]. The goal of the agent is to exit the Wumpus world alive. The agent can exit the Wumpus world by reaching room [4,4]. The wumpus world contains exactly one Wumpus and one pit. There will be a breeze in the rooms adjacent to the pit, and there will be a stench in the rooms adjacent to Wumpus.

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/cd6b68dc-c79f-4dcb-8126-04da90d65912)

<center>Wumpus World Representation</center>
<p>
This is a python program that uses propositional logic sentences to check which rooms are safe. 

It is assumed that there will always be a safe path that the agent can take to exit the Wumpus world. The logical agent can take four actions: Up, Down, Left and Right. These actions help the agent move from one room to an adjacent room. The agent can perceive two things: Breeze and Stench.
</p>

<hr>
<h1>Sample Input and Output:</h1>
<hr>

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/8696111a-a4a7-47cb-ba4b-43a4ef88573f)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/4be5bf06-79fa-4fa0-9334-38a33f06060b)

## PROGRAM :
```
wumpus = [
    ["Save", "Breeze", "PIT", "Breeze"],
    ["Smell", "Save", "Breeze", "Save"],
    ["WUMPUS", "GOLD", "PIT", "Breeze"],
    ["Smell", "Save", "Breeze", "PIT"]
]

r = c = 0
arrow = True
score = 0
moves = {'u': (-1, 0), 'd': (1, 0), 'l': (0, -1), 'r': (0, 1)}

while True:
    choice = input("u-up d-down l-left r-right: ")

    if choice not in moves:
        print("move denied")
        continue

    dr, dc = moves[choice]
    nr, nc = r + dr, c + dc

    if 0 <= nr < 4 and 0 <= nc < 4:
        r, c = nr, nc
    else:
        print("move denied")

    print("current location:", wumpus[r][c])

    if wumpus[r][c] == "Smell" and arrow:
        if input("Throw arrow? y/n: ") == "y":
            d = input("Arrow direction u/d/l/r: ")
            dr, dc = moves.get(d, (0, 0))
            x, y = r + dr, c + dc

            if 0 <= x < 4 and 0 <= y < 4 and wumpus[x][y] == "WUMPUS":
                print("Wumpus killed!")
                score += 1000
                wumpus[x][y] = "Save"
                wumpus[1][0] = wumpus[3][0] = "Save"
            else:
                print("Arrow wasted!")
                score -= 10

            print("Score:", score)
            arrow = False

    if wumpus[r][c] == "WUMPUS":
        score -= 1000
        print("Wumpus here! You died.")
        print("Score:", score)
        break

    if wumpus[r][c] == "GOLD":
        score += 1000
        print("GOLD FOUND! You won!")
        print("Score:", score)
        break

    if wumpus[r][c] == "PIT":
        score -= 1000
        print("You fell in the pit!")
        print("Score:", score)
        break
```
## OUTPUT:
<img width="1917" height="1158" alt="image" src="https://github.com/user-attachments/assets/2d94ec8f-6e9e-49e1-8b15-e27cbd971376" />

## RESULT :
Therefore the program to execute using wumpus world theorem has been executed successfully.
