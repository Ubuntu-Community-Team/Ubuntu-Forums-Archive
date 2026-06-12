---
title: "Appearance Preferences"
date: 2009-08-17
forum: General Help
---

### Post by Mutil8r on 2009-08-17
Hey guys, another problem I encoutered.

I was trying to enable Desktop effects. After choosing, it tells me to enable my Nvidia driver *it was disabled? didnt notice* anywaiz, until this pops up. 

SystemError: Failed to lock /var/cache/apt/archives/lock

Any1 know how to fix this?

---

### Post by Bradj47 on 2009-08-17
Do you have Compiz installed? (Compiz is a graphics driver) I wasn't able to enable this until I installed Compiz. Though I do have an ATI so I'm not sure if its the same with your NVidea.

---

### Post by Mutil8r on 2009-08-17
will try. Thanks for replying

---

### Post by Bradj47 on 2009-08-17
No problem. But I forgot to mention something. When I installed Compiz when I was running 8.04 (Hardy) it screwed up my system but I had no problems with 9.04 (Jaunty). So... if you're using 8.04 I hope you read this before you try it...

---

### Post by Mutil8r on 2009-08-17
Im using Jaunty O.O

Well, nothing happended. Its still like that. Same error. Some1 help pls.

---

### Post by fooman on 2009-08-17
do you have synaptic package manager, update manager or add/remove open?

if so,  close it and then try to enable the driver again.

when you enable the driver,   it downloads the appropriate driver using the package manager....if you already have add/remove, update manager or synaptic open,  it will not work.

you can only have one package manager open/running at a time.

hope that helps.

---

### Post by Mutil8r on 2009-08-18
yeah, I made sure of that. But now I get a new error. When I try to enable my driver it automatically Downloads and install it then freezes and a pop up shows saying

Sorry, the Jockey backend crashed. Please file a bug at:

  ubuntu-bug jockey-common

Trying to recover by restarting backend.

---

### Post by Mutil8r on 2009-08-18
bump

---

### Post by 3rdalbum on 2009-08-18
All the Hardware Drivers program does, in relation to Nvidia drivers, is installs the "nvidia-glx-180" package (assuming your card is 6xxx series or better). You might as well just go into Synaptic and install that package, it will accomplish the same task.

---

