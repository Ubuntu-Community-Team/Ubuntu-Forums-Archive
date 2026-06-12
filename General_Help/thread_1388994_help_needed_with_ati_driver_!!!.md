---
title: "help needed with ati driver !!!"
date: 2010-01-23
forum: General Help
---

### Post by pirlo89 on 2010-01-23
hello :) , i am new to ubuntu so bare with me ...

i have installed ubuntu 9.10 and everything was going ok. then i have found out that when i use a program that depends on opengl i get like blank spots on my screen. so i went to the ati website , downloaded the catalyst and then tried to install it only to find out that it needs an earlier version of ubuntu to run. 

so far i have been using compiz and the visual effects works great set on extra. i restarted my computer , signed in , the visual effects are disabled and cannot be enabled. i have installed "EnvyNG" to fix it , but no success there .

so i guess the solution would be to re-install open source  driver, but how ?

**[COLOR=Red]P.S. : i have an ati radeon x1600 video card.[/COLOR]**

---

### Post by rogue_0111 on 2010-01-23
this may be of some use:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by c0mput3r_n3rD on 2010-01-23
Unfortunately ATI has bad support for Linux, and you're not going to be able to use the fglrx ati driver unless you're running 8.10 or earlier.  Sorry dude.

---

### Post by Mark Phelps on 2010-01-24
> **pirlo89 said:**
> hello :) ... so i guess the solution would be to re-install open source  driver, but how? ...

Follow the instructions in the following link:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by JSeymour on 2010-01-24
> **c0mput3r_n3rD said:**
> Unfortunately ATI has bad support for Linux, and you're not going to be able to use the fglrx ati driver unless you're running 8.10 or earlier.  Sorry dude.Sorry, dude, you're flat wrong: [Getting Dual-Head, "Big Desktop" Working]("http://ubuntuforums.org/showthread.php?t=1376129").  I didn't mention it in that article, but that's on Ubuntu 9.10 Desktop.

Jim

---

### Post by LoloftheRings on 2010-01-24
Yea fglrx works on 9.10. No problems here.

I installed fglrx through the Hardware Drivers dialog (System -> Administration -> Hardware Drivers) without an issue, it couldn't be much easier.

---

