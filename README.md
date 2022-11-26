# Game-bingo
copy code ไปเล่นได้เลยครับ

from turtle import *



turns = {'red': 'yellow', 'yellow': 'red'}
state = {'player': 'yellow', 'rows': [0] * 8}


def grid():
    
    bgcolor('light blue')

    for x in range(-150, 200, 50):
        print(x, -200, x, 200)

    for x in range(-175, 200, 50):
        for y in range(-175, 200, 50):
            up()
            goto(x, y)
            dot(40, 'white')

    update()


def tap(x, y):
    
    player = state['player']
    rows = state['rows']

    row = int((x + 200) // 50)
    count = rows[row]

    x = ((x + 200) // 50) * 50 - 200 + 25
    y = count * 50 - 200 + 25

    up()
    goto(x, y)
    dot(40, player)
    update()

    rows[row] = count + 1
    state['player'] = turns[player]


setup(420, 420, 370, 0)
hideturtle()
tracer(False)
grid()
onscreenclick(tap)

