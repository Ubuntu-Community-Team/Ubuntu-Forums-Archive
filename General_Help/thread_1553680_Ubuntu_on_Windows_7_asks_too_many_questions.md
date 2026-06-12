---
title: "Ubuntu on Windows 7 asks too many questions"
date: 2010-08-15
forum: General Help
---

### Post by houldsworth1 on 2010-08-15
I just installed Ubuntu within Windows 7.  I actually thought it would run alongside it and I could switch back and forth in that cool way you can on Apples....guess I should have RTM.

Anyway, when I boot it asks me if I want Windows 7 or Ubuntu, as expected.  But after I select Ubuntu it asks me to select from 4 other options (native Linux, something about Windows - can't remember the details).  I picked the first one and everything seems OK, but the documentation doesn't mention these at all.

Anyone else have this?

---

### Post by celldweller1591 on 2010-08-15
What you see at-first is the Win7 boot manager aka windows bootloader. After you select Ubuntu, you see linux native loader called as GRUB. If you really see Grub annoying, you can make it not show its face to you at all. 
Open terminal and type :"sudo /etc/default/grub" and decrease the GRUB_TIMEOUT to 0 seconds and save the file & you will not be prompted on boot with Grub at all.

---

### Post by J V on 2010-08-15
1: If you want to "Switch between" the 2 OS, you have to install it in a virtual machine (Google vbox)

2: The first menu is the windows selection, the second is grub: The linux selection.

You can ignore this and take the top option every time (And install startupmanager to shorten the wait time to 0 seconds)

---

### Post by houldsworth1 on 2010-08-15
Got it!  Thanks guys - you're the best!

---

### Post by wilee-nilee on 2010-08-15
> **celldweller1591 said:**
> What you see at-first is the Win7 boot manager aka windows bootloader. After you select Ubuntu, you see linux native loader called as GRUB. If you really see Grub annoying, you can make it not show its face to you at all. 
Open terminal and type :"sudo /etc/default/grub" and decrease the GRUB_TIMEOUT to 0 seconds and save the file & you will not be prompted on boot with Grub at all.

Setting the grub timeout to 0 is always a bad idea, this just leaves you without some options in case of problems, even in a wubi environment.

Thread starter please note that wubi is for trying out Ubuntu, it runs slower in this manner and you're subject to Windows always working.

---

### Post by houldsworth1 on 2010-08-15
> **wilee-nilee said:**
> Setting the grub timeout to 0 is always a bad idea, this just leaves you without some options in case of problems, even in a wubi environment.

Thanks.  I wasn't planning on doing that - just wanted to know why it was asking me more questions than the documentation states.  I think that is going to confuse people (it did me) - especially if they are not the sort to speak Klingon. :D

---

### Post by Marlonsm on 2010-08-15
> **wilee-nilee said:**
> Setting the grub timeout to 0 is always a bad idea, this just leaves you without some options in case of problems, even in a wubi environment.

Thread starter please note that wubi is for trying out Ubuntu, it runs slower in this manner and you're subject to Windows always working.

Just set it as 1, then. If there is any problem, just keep pressing any button and when it reaches Grub, the countdown will stop.

BTW, the command should be:
```
sudo gedit /etc/default/grub
```
if you're using the normal Ubuntu.
If you're using Kubuntu, just change "gedit" for "kate".

---

### Post by celldweller1591 on 2010-08-15
@[Marlonsm]("http://ubuntuforums.org/member.php?u=792604") My bad :)

---

### Post by WorMzy on 2010-08-15
Actually, if you want to be correct, it should be ```
**gksu** gedit /etc/default/grub
``` or ```
**kdesu** kate /etc/default/grub
``` "sudo" should only be used for CLI applications, such as nano, vi, etc.

---

### Post by slooksterpsv on 2010-08-15
I thought it was supposed to be:
```

gksudo [gui app] (other args)

```

GKSUDO instead of GKSU

---

### Post by WorMzy on 2010-08-15
Either is fine, since Ubuntu has it set so that gksu uses sudo (rather than su) as it's backend anyway; so gksu and gksudo are essentially the same thing. The only difference it'd make if it used the su backend is that it'd ask for root's password, rather than the sudoers password.

---

