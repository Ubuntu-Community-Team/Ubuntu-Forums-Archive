---
title: "can't open anything from the places"
date: 2009-09-07
forum: General Help
---

### Post by argiris on 2009-09-07
hi to all of you. first of all i am a new user of ubuntu. yesterday i installed ubuntu 9.04 throught windows to check if everything was fine and if it is user friendly. so i checked all the stuff in ubuntu and everything worked fine (exept from the mp3s, but i think if i had an internet connection this could be solved with the right plug in. nevermind) and today i desided to install it as the main os . 

after the installation finished, i restarted the computer and after some time (2-3 mins) ubuntu started. everything looked nice the administrator and the application tools, programms , firefox etc  but i couldn't reach any of the places folder (computer,documents, not even my ipod). as i saw i could navigate to documents and other folders through an application but i can open it as a separate window. the fact is i can't open it at all.  i restarted my computer but nothing happends.

i cant imagine what happends.

do i have to reinstall the os??  what can i do now?

thank you .

---

### Post by fluffman86 on 2009-09-07
Option 1: Go to Applications > Accessories > Terminal and type
```
nautilus
```
Let us know what happens and post any output here. 

Option 2: Just go ahead and reinstall.  Something may have gone wrong during the install.  Did you wipe the whole hard drive to install?  Since you just installed, chances are you don't have much to lose.

---

### Post by argiris on 2009-09-07
i typed it . i get the message .. segmentation fault 

yes i used whole of the disk for the installation.

---

### Post by c0mput3r_n3rD on 2009-09-07
open terminal; Applicatoins -> Accessories -> Terminal  and type "ls -l".  The beginning part of all the listings will look something like this "drwxrwxrwx" or "-rwxr-xr--".  If the 2nd "-" (assuming all the places are default to a "-"), then you do not have permissions to look at the contents.  If this is so, type "chmod 755 ~" (with out quotes).  See if that helps/if it's a permissions problem.

---

### Post by drs305 on 2009-09-07
Do you have a CD/DVD in the tray? I know it sounds odd, but if you do, remove it and try using Nautilus again.


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by argiris on 2009-09-07
all of the places contents like video,music etc have the ''drw xrw..... '' format
but the     examples.desktop has a  "-rwxr-xr--" .

> Do you have a CD in the tray? I know it sounds odd, but if you do, remove it and try using Nautilus again

no i havent . i checked it again but nothing happend . the same segmentation fault.


edit..
!!!!!!!!!!!!!!! hey man i am too full!!!! 
i had a blank cd in the 3rd slot.
now the folders opened !!!!



thank you very much. i appreciate your help .

thanks 2 all of you.

---

