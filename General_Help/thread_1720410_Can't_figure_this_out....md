---
title: "Can't figure this out...???"
date: 2011-04-03
forum: General Help
---

### Post by robertcoulson on 2011-04-03
Take a look at the attachments...Don't know why this is happening...Any help would be appreciated. I use Ubuntu 10.10
Thanks, Robert

---

### Post by Timmer1240 on 2011-04-03
Did you try do what it is telling you to do?

---

### Post by robertcoulson on 2011-04-03
Yes..I sure did (about 6 different times)..But it keeps coming up..?
Robert

---

### Post by Timmer1240 on 2011-04-03
try opening a terminal and entering sudo apt-get update

---

### Post by robertcoulson on 2011-04-03
Well..I tried that and the terminal asked me to put 11.04 in and hit enter...Went back to update manager and still have the same error...??
Robert

---

### Post by Timmer1240 on 2011-04-03
try sudo dpkg --configure -a

---

### Post by Rubi1200 on 2011-04-03
Go to System > Administration > Synaptic Package Manager > Settings > Repositories > make sure there is no check-mark next to installable from CD and then try updating again.

If that doesn't work post the contents of /etc/apt/sources.list

---

### Post by robertcoulson on 2011-04-03
Timmer1240, that didn't work either..Guess I will just have to live with that error...Thanks for trying to help.
Robert

---

### Post by robertcoulson on 2011-04-03
Rubi1200...That worked perfectly...Thanks so much, and to all that helped, thanks.
Robert

---

### Post by Timmer1240 on 2011-04-03
well I tryed I knew someone would pop in that knew though!

---

### Post by Rubi1200 on 2011-04-03
> **robertcoulson said:**
> Rubi1200...That worked perfectly...Thanks so much, and to all that helped, thanks.
Robert
No problem, you are more than welcome :-)

And good work on the part of Timmer1240 too; nothing wrong with the ideas he suggested.

---

### Post by robertcoulson on 2011-04-03
Hey timmer1240, that was your next step...Right..Thanks again.
Robert

---

### Post by Timmer1240 on 2011-04-03
Actually Ive had a few update errors those worked to solve my errors good work rubi1200 for his solution!

---

### Post by Julian Luna on 2011-04-03
[SIZE=1]I don't wanna sound rude but... is there any good argument to try out the beta release which isn't released already and will probably be stable around july? D: Because then I'm probably moving to 11.04 too... btw i'm not exactly wise about ubuntu but why update-manager need CD to install updates? :/ AMD is all about a graphic card right? Did you try already installing the proper "Aditional Drivers" Which are on System -> Administration?[/SIZE]

---

### Post by robertcoulson on 2011-04-03
It might have happened when I installed 11.04 in Virtual Box...???
Robert

---

