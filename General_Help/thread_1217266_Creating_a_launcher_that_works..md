---
title: "Creating a launcher that works."
date: 2009-07-19
forum: General Help
---

### Post by JJNova on 2009-07-19
Apparently I don't comprehend creating a launcher. I recently purchased a game called My Tribe. In order to play the game, I navigate to /home/My Tribe/run.cmd

My wife thoroughly enjoys the game, and I would like to setup a shortcut in the Application>Games menu so she could quickly, and easily launch the game. Unfortunately, whenever I set one up, it errors out. Even if i create a shortcut to /home/My Tribe/run.cmd and place it on the desktop it wont work. 

The shortcut will work if I run it from the same directory as the original file.

When I attempt to use the application launcher, I get the error that "child processes could not be ran. Directory doesn't exist." 

Any suggestions ?

---

### Post by The Cog on 2009-07-19
Try a launcher with this command:
**sh -c 'cd /home/My\ Tribe ; ./run.cmd'**
I suspect it's necessary to change directory before running the game.

---

### Post by JJNova on 2009-07-20
> **The Cog said:**
> Try a launcher with this command:
**sh -c 'cd /home/My\ Tribe ; ./run.cmd'**
I suspect it's necessary to change directory before running the game.

Thank You. Your assistance has been greatly appreciated, and your suggestion worked flawlessly. Everything is as it should be.

---

