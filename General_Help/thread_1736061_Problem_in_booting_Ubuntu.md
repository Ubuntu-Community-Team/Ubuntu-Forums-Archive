---
title: "Problem in booting Ubuntu"
date: 2011-04-22
forum: General Help
---

### Post by piyush.neo on 2011-04-22
i am using Ubuntu 9.10 and it was working fine until now . Suddenly i am unable to boot. As soon as i select Ubuntu from Grub menu , it shows the Ubutnu symbol for some time ( while booting) and after it nothing......just a blank screen.
Can any body suggest anything or where to start looking from.
PS: i have windows installed too which is working fine.

---

### Post by lmarmisa on 2011-04-22
Are you able to open a tty terminal?. 

Wait until you get the black screen and then type "**Ctrl+Alt+F1**" right through to "**F7"** to select the different tty terminals.

---

### Post by piyush.neo on 2011-04-22
> **lmarmisa said:**
> Are you able to open a tty terminal?. 

Wait until you get the black screen and then type "**Ctrl+Alt+F1**" right through to "**F7"** to select the different tty terminals.

No i cant open the terminal.i am not  even getting the login screen.

---

### Post by lmarmisa on 2011-04-22
Have you tried to boot selecting the recovery mode?.

---

### Post by ddude117 on 2011-04-22
I had this issue to with ubuntu 9.10 ue . i couldnt find a sollution so i just put in my ubuntu install disk , backed up my files onto a hdd using the trail mode thing then reinstalled ubuntu then put my files back :guitar:

---

### Post by piyush.neo on 2011-04-22
> **lmarmisa said:**
> Have you tried to boot selecting the recovery mode?.
yes i have tried. It booted and landed to shell with promt something like **initram>**.
i tried executing **fcsk** but it is showing error 
/bin/sh: can't find fcsk
Then i checked out the location of fcsk command from another ubuntu machine and tried
**/sbin/fcsk**
still command not found. :(

---

### Post by lmarmisa on 2011-04-22
Boot into a Ubuntu Live CD, then visit this page [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) , run the Boot Info Script and post here the results (follow the instruction of that page).

---

