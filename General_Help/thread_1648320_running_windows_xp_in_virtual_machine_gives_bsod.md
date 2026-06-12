---
title: "running windows xp in virtual machine gives bsod"
date: 2010-12-18
forum: General Help
---

### Post by termin on 2010-12-18
okay, i just finished successfully installing a virtual machine and windows xp. the windows setup finished no errors, but now when i try to boot up it gives me the blue screen of death (see attachment). after the bsod it just reboots.


help please?


note: in the screenshot it doesn't look blue but it is. i couldn't pause it so then it would show blue so it ended up black.

---

### Post by termin on 2010-12-18
edit:

included the full blue screen of death message


in attachment

---

### Post by wilee-nilee on 2010-12-18
Try the f8 key to get to the safe mode you can try to get in that way or just in the command run a chkdsk /f/r it will ask if you want to run it at startup say yes.

---

### Post by termin on 2010-12-18
thanks or quick replay, i ran in safe mode and still no fix :(

---

### Post by wilee-nilee on 2010-12-18
> **termin said:**
> thanks or quick replay, i ran in safe mode and still no fix :(

how about the chkdsk /f/r

---

### Post by termin on 2010-12-18
im reallly sorry for bugging you, but how do i do this?
i ran:
virtualbox chkdsk /f/r in terminal

and it just started up as normal.

---

### Post by fatal_ERROR777 on 2010-12-18
It looks like the CD (or any other source where you got the .iso file) is broken or when you installed windows a parallely running program has caused some problems. Have you tried reinstalling Windows? 
[SIZE="1"]I am a total noob, so I won't help you so much[/SIZE]

Fatal_Error

---

### Post by wilee-nilee on 2010-12-18
> **termin said:**
> im reallly sorry for bugging you, but how do i do this?
i ran:
virtualbox chkdsk /f/r in terminal

and it just started up as normal.

What started up as normal?

What terminal?

You have a command terminal in the f8 safe mode before choosing a login open it and run the chkdsk /f/r

It may be a bad install or a lot of things. have you used this disc to install with successfully before?

---

### Post by termin on 2010-12-18
thanks, this worked for me fine. sorry for the trouble if i was acting a little bit dumb on that last response.

---

### Post by wilee-nilee on 2010-12-18
> **termin said:**
> thanks, this worked for me fine. sorry for the trouble if i was acting a little bit dumb on that last response.

Hey glad its running.;) It is difficult to always post the exact stuff or what we mean.

---

