# Dots_And_Boxes_RL
RL Q learning to imitate the playing of game


## Assumptions and inits
- 3x3 dots and 4 boxes and so 12 lines
- ***NOT***: 6 moves for each player
- 2 pow 12 states for the game
- DRAW / TIE is available in our implementation
- Our agent vs itself
## Procedure
- Init Q table
- Give a game state
- Choose actions for each state and store the reward n next state
- At the end of game, update the Q table //reverse chronological for fast updates
- Repeat playing to ensure that all states are visited many many times

## Confusions and design choices
- State should consist of what parameters
    - Like the current points also? (but it doesn't matter if you have to maximise the future points)
- Actions - count differs for each state
    - 010101100111 ===> 1 line is there.. 5 zeros -> 1,3,5,8,9 actions available
    - 1 to 12 from left 
- 4096 entries -- binary encoding or bitstring
- Table 
    - STATE rows and ACTIONS columns????
    - HASHMAP states, value ==> dictionary {action1: qvalue,action2:qvalue}
    - Transition function takes as input state and action ==> gives next state .... 0,2=>output as 2nd bit set
- Reward definition
    - NOT TO BE USED:::GOAL STATE -- reward 100 and remaining 0
    - 100 points, -100 points, 0 points //long term benefit (alternate reward and penalty)
    - adv : reward is 0 for other cases
    - OPTIONAL: you lose one box -1 reward, you gain one box +1 reward  // short term benefit
    - OPTIONAL: ONLY reward, not penalty
- ####Actions
    - Current state, possible actions == which has the highest Q value??
    - Dis: Exploitation... All states not visited
    - Simple learner..: visit count maintained.. and find which is less..
    - Random learner.. 
    - Q learner...
    - CHOICE  : that k method in tom mitchell
- INIT FILLING all zeros
- END OF game : all 12 are 1's ==> end of episode, updating done
- SCORE MAINTAINING: one for each box taken, 12 lines over... decide the winner and give rewards
- DISCOUNT RATE --0.8 
- LEARNING RATE --0.2 


---
### VARIABLE , tables
    - TABLE : hashtable, key: state(4096), value: action-qvalue pairs // permanent for all training and test
    - GAME EPISODE: we have to store, memory for player 1 and 2 {state, action, nextstate, reward}
    - SCORE of each player after each box is filled -- > decide winner
    - Current player =player 1 or player 2
    - CURRENT board STATE
### FUNCTIONS
#### learner:
    - init QTABLE 
    - while 1 million games:
        play game
    - save QTABLE 
    - playwithHuman
#### Game:
    - init board state
    - init players as p1,p2 or p1,human
    - init current player = p1
    - init box [0 0 0 0]
    - while not final state: 
        - if cp != 'human' : 
            currentplayer.make move // simple, q learner , random .. 3 boxes..
        - else:
            accept input
        - update currentplayer.memory
        - Check if new box formed, update player score
        - else 
        -   toggle the currentplayer
        - update board state with current move
    - update QTABLE with rewards and penalties

#### check if new box 
(box,newstate){
    for  i = 0 to 3:
        i==0 and box[i]==0:
            if newstate 1378 set: 
                update
}

#### update memory 
-  

#### update Qtable
- 

#### Make MOVE




    

