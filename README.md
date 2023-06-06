# Off-policy-Monte-Carlo-Control-Racetrack
1. The task environment includes racetrack and race car. Racetrack are the cells in the diagram, and race car could be at one of a discrete cell position of racetrack. Also, race car has its velocity, which is simplified to be a number of grid cells moved horizontally and vertically per time step. Therefore, we got:\
  The state of the task environment: (position, velocity). (factored representation of state)\
  The state space: all the allowed combinations of (position, velocity).\
  The initial state: being in starting line of racetrack with zero velocity.\
  The finish state: crossing the finish line of racetrack.\
  The rewards: -1 each step for action that agent takes until the car crosses the finish line.
 
2. The Agent who interacts with the task environment actually is the racer: me or program. The agent could implement an action to the environment based on the current state following a behavior policy. We simplified the actions to be 3x3 possibilities: each may change velocity by +1, -1, or 0 horizontally and vertically. Since there are constraints for our velocity: both velocity components is nonnegative and less than 5 ( 0<=V<=4), our actions would be:\
  The actions of the agent: given the current velocity, all the actions that would satisfy the constraints of our velocity.

3. The goal, which is about how we measure the racer’s performance, is that race car can go as fast as possible (got the highest reward) meanwhile not so fast as to hit the wall.

4. One more assumption is that when hit the wall, the race car will be back to a start position (randomly one) without any punishment.

5. The learning strategy is Off-policy every-visit MC control. Several hyper-parameters have to be considered before running algorithm: \
  epsilon: 0.1.\
  gamma: 0.9. (no discount has been tried, the result is worse than the one with discount)\
  episode number: running with incremental episode number.\
  initial target policy: randomly initialize the target policy.\
  initial Q table: initialize Q table with negative -60 to speed converging.\
  racetrack = the smaller racetrack from Exercise 5.12 of the book (Reinforcement Learning: An Introduction second edition Richard S. Sutton and Andrew G. Barto).
