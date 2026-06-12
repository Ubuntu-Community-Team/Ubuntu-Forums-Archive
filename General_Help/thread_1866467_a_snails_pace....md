---
title: "a snails pace..."
date: 2011-10-21
forum: General Help
---

### Post by K4NEB on 2011-10-21
i have upgraded from 10.04 to 10.11 using the upgrade via the update manager.

with 10.04 everything was super fast  lightening speeds! that made me a happy bunny :D

now with 10.11 i click on a program ie fire fox and then some time later it opens.

clicking on the drop down menus takes for ever they freeze and stick 

and all the time my computer is whirring away as if its trying to launch to the moon! like its running loads of processes somewhere in the back ground

all this equals unhappy bunny :(

i left stupid windows for that reason :(

if i open the terminal and enter top nothing is hardly draining, and yet its still plodding along like a tortoise :(

can some one shed some light on this for me please.

any idea if a fresh install from a cd would be better than to have updated via update manager?

---

### Post by hwttdz on 2011-10-21
Take a look at iotop, or the %wa in the header in top?  It's possible the slowdown is due to io.

There are fewer variables in a fresh install, so in a way it's easier to figure out, but in theory they're the same.  

Also take a look at gnome-system-monitor (that's still around isn't it?) and look at your memory usage, swap usage, well really just browse around there and see if anything jumps out.

---

### Post by K4NEB on 2011-10-22
im surprised this post actually posted as it froze when i hit the submit button.

hmmm i still cant seem to figure out what its doing :(

---

### Post by drawkcab on 2011-10-22
In another thread folks were discussing a possible unity memory leak.  Try logging into another desktop and see what happens.

---

