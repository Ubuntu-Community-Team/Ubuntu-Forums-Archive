---
title: "Unable to get exclusive lock  This usually means that another package management appl"
date: 2009-10-19
forum: General Help
---

### Post by valencc7 on 2009-10-19
I everyone !!  I am new to UBUNTU but so far I love it!  I am having a problem trying to install new software or using commands in  the terminal.  This is the message that  I normally get when trying to install new softare. Unable to get exclusive lock

"Unable to get exclusive lock This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first."  However I get this even if I dont have any termianl open.

Can anyone help ??  I using the latest UBUNTU

---

### Post by oboedad55 on 2009-10-19
> **valencc7 said:**
> I everyone !!  I am new to UBUNTU but so far I love it!  I am having a problem trying to install new software or using commands in  the terminal.  This is the message that  I normally get when trying to install new softare. Unable to get exclusive lock

"Unable to get exclusive lock This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first."  However I get this even if I dont have any termianl open.

Can anyone help ??  I using the latest UBUNTU

Do you have synaptic package manager or update manager open? That would cause the error.

---

### Post by valencc7 on 2009-10-20
I have them closed.  I even restated the pc.  Do basically I can not install new software from the synaptic manager and can't use the terminal to perform some operations.  Thanks for your efforts.

---

### Post by undecim on 2009-10-20
Do you have automatic updates (without confirmation) set up? If you are updating, you won't be able to install new software during that time

---

### Post by theozzlives on 2009-10-20
Run:
```
sudo dpkg --configure -a
```
you probably got packages that didn't install completely (or broken packages).

---

### Post by tolea on 2010-01-15
I allso have this problem
I can't install any new packages ... exept those installed through the terminal... 
Can someone help me with this problem ... 
I'm just a beginer ... you can say that it's my first linux experience

---

### Post by tolea on 2010-01-15
and i dont have automatic updates... in generali i turnd off the feauture

---

### Post by myrmidon666 on 2010-11-28
Not sure if this problem got resolved but, I found a solution for this problem [here]("http://ubuntuforums.org/showthread.php?t=1029701").

---

