---
title: "Windows messed up"
date: 2010-04-28
forum: General Help
---

### Post by bigseb on 2010-04-28
I must have done something to my window settings cos those three buttons in the top right corner (minimize, maximize and close) are gone. I also cannot resize the window or move it around using the mouse :( What did I do? And more importantly how do I fix this?

:(

[ATTACH]154586[/ATTACH]

:(

---

### Post by arrrghhh on 2010-04-28
Are you running Lucid or Karmic?  Did you try changing any settings that relate to where those buttons are located?  Make any theme changes, etc?

---

### Post by spiky001 on 2010-04-28
what happens if you press F11

---

### Post by sisco311 on 2010-04-28
Press Alt+F2 and run:
```
metacity --replace
```

---

### Post by mhgsys on 2010-04-28
Just disable extra effects; 

System>Preferences>Appearance> tab Visual effects, 

set them to None, panels and buttons should be back

if you want the option to be on extra ; set them to none and reboot

once booted/
Set effects on  extra again 

I also had this "problem" a few times on my ati card/
Don't know why ; but this worked out for me.

---

### Post by bigseb on 2010-04-28
> **arrrghhh said:**
> Are you running Lucid or Karmic? Did you try changing any settings that relate to where those buttons are located? Make any theme changes, etc?

Karmic

Did make any changes specifically but I tend type faster than I can think so I prolly hit th wrong key at some point. Can't say for sure though.

No theme changes


> **spiky001 said:**
> what happens if you press F11

FF goes into fullcreen mode. Nothing happens to the other windows.

---

### Post by bigseb on 2010-04-28
> **mhgsys said:**
> Just disable extra efects; 

System>Preferences>Appearance> tab Visual effects, 

set them to None, panels and buttons should be back

if you want the option to be on extra ; set them to none and reboot

once booted/
Set effects on  extra again 

I also had this "problem" a few times on my ati card/
Don't know why ; but this worked out for me.


  WORKED...  thanks, you've just won my eternal love and devotion.

My graphic card is Nvidia not ATI btw and also I didn't reboot. Will try that later.


:guitar:

---

### Post by mhgsys on 2010-04-28
Great, I like eternal devotion  lol 

Also wanted to say; I had the same problem on my ati** and** nvidia geforce. (last time it happened was on my ati radeon)
Anyway; I guess..it's basically compiz / extra effects f*cking up...
Restarting gdm only does not solve it though,that's why the reboot 
So. I'm waiting for you to reboot, and set the effects to extra again.

That always worked out fine for me.

Hoping and wondering if it's the same for you.

---

