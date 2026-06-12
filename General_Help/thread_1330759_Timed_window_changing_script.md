---
title: "Timed window changing script"
date: 2009-11-18
forum: General Help
---

### Post by kradalby on 2009-11-18
Hi

I was setting up netbook with ubuntu nbr the other day, and im thinking of using it as a simple htop server monitor. 

The only thing is that i have two servers.


Right to the question.

Can someone link me to or help me find a way to make a sh script or something that changes from terminal window 1 to terminal window 2 every x minutes? dont know if u just can write in the alt + tab function?

thank you!

please move this thread if it is posted at the wrong section.

Kristoffer

---

### Post by diesch on 2009-11-18
From
```
wmctrl -l -p|grep Terminal
``` pick the window IDs (first column) of the terminals you want to switch to and then use
```
wmctrl -i -a $WINDOW_ID
``` to switch to that terminal.

---

### Post by kradalby on 2009-11-19
Awesome thnx

---

