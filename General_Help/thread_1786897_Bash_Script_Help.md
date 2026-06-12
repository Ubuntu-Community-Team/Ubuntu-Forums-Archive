---
title: "Bash Script Help"
date: 2011-06-20
forum: General Help
---

### Post by hunter.allen on 2011-06-20
Hello everyone. I am trying to write a bash script to run the PlayerStage project. I just want to get three programs running. They have to be going at the same time, which is beyond my bash skills... 

Here is my current script:

#!/bin/bash
#This script brings up the player driver. (Ya. I'm lazy.)

cd ~/Code/Eli
#Bring up the robot on the localhost. (Port 6665)
player stage.cfg
#Bring up the planner proxy on the same host. (Port 6666)
player wavefront.cfg

#Now that both servers are established, bring up PlayerNav.
playernav localhost:6665 localhost:6666

---

### Post by Lars Noodén on 2011-06-20
Putting an ampersand (&) after each program will cause it to run in the background.

e.g.

player stage.cfg

becomes

player stage.cfg &

and will run in the background.

---

### Post by _0R10N on 2011-06-20
Hi, I'm unfamiliar with PlayerStage, so probably I'm not the best option to answer this but I can help you with your scripting, so what's the problem with the one you posted, what error message is prompted?

---

### Post by hunter.allen on 2011-06-20
Well, the ampersand didn't work... I don't know why, but it didn't... The PlayerStage project is a mobile robotics platform. It is a server that communicates to the robots.

---

### Post by galvatron408 on 2011-06-20
#!/bin/bash -x
# adding -x puts you in to verbose so you can see things executing
#This script brings up the player driver. (Ya. I'm lazy.)

cd /home/user/Code/Eli #use the absolute path, not ~
#Bring up the robot on the localhost. (Port 6665)
player stage.cfg #are you sure this is an executable? It looks like a config file
#Bring up the planner proxy on the same host. (Port 6666)
player wavefront.cfg #same thing here, looks like a config file

#Now that both servers are established, bring up PlayerNav.
playernav localhost:6665 localhost:6666

---

### Post by _0R10N on 2011-06-20
Well, can you tell us whether executing each command from a console works?

---

