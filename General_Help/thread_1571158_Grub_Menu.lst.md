---
title: "Grub Menu.lst"
date: 2010-09-09
forum: General Help
---

### Post by FinalShot on 2010-09-09
I want to remove the default boot time from grub, I created /boot/grub/menu.lst, but I'm unsure what I can put in here to remove the countdown.

---

### Post by gandaran on 2010-09-09
you can also do this using startup manager, install from the repositories

---

### Post by mohansathish on 2010-09-09
Hello Finalshot

You manually created menu.lst? 
What version of ubuntu are you using? If its 9.04 or before, you can edit codes in menu.lst.

If its 9.10 or 10.04, then you must look at /boot/grub/grub.cfg

you can find countdown=10 in that file. you can edit it by accessing it as root(or change file permissions ;))

and my kind request is, when you got correct answer for your post, please hit *thread tools* at the top and set it as *solved*.

---

### Post by Rubi1200 on 2010-09-09
If Ubuntu is the only operating system on the computer then you can do this:

```
sudo gedit /etc/default/grub
```Find this line:

```
GRUB_HIDDEN_TIMEOUT=0
```and remove the comment # at the beginning.

Save and then run

```
sudo update-grub
```The next time you boot there will be no GRUB menu and the system will boot directly into Ubuntu.

If the line is already uncommented then change this:

```
GRUB_TIMEOUT=10
```
to this

```
GRUB_TIMEOUT=0
```

Then as above.

---

### Post by FinalShot on 2010-09-09
Thanks mohansathish, about to reboot now.

@Rubi1200
Did you read my OP, I didn't want to remove Grub, I just wanted to remove the timer...

---

### Post by mohansathish on 2010-09-09
Finalshot, when you set the timeout as 0, then it is the same as making grub to not to load the boot screen. know this and if had done the change, revert it to the way you need. the minimum timeout must by at least 1 second

---

### Post by Rubi1200 on 2010-09-09
> **FinalShot said:**
> Thanks mohansathish, about to reboot now.

@Rubi1200
Did you read my OP, I didn't want to remove Grub, I just wanted to remove the timer...
First, you are not supposed to edit the file that mohansathish suggested (there is a line at the beginning of the file that warns against editing it).

Second, my instructions do NOT remove GRUB, but only the timer/countdown.

Good luck!

---

### Post by FinalShot on 2010-09-09
Well then how do I remove the timer, and have grub load?

---

### Post by mohansathish on 2010-09-09
Hello Rubi,

you are correct that we should not edit the codes and if there is any urge to edit them, we must have a backup of the older one so that it will help us to revert back and thanks for pointing that :)

cheers

and finalshot,

you want the boot screen to not to load at the beginning and to not to wait for your command to boot the first option, set timeout to 0 and thats what Rubi is telling you (:

---

### Post by Rubi1200 on 2010-09-09
> **FinalShot said:**
> Well then how do I remove the timer, and have grub load?
Is Ubuntu the only OS on your computer?

Do you want to "see" the GRUB menu with the default 10 second countdown?

OR, do you want to boot directly into Ubuntu without the countdown and without seeing the menu (but retaining GRUB obviously)?

---

### Post by FinalShot on 2010-09-09
.... I have multiple OS's installed, so I need the boot menu, I just want to remove the timer. So it doesn't boot the selected option in 10 seconds...

---

### Post by Rubi1200 on 2010-09-09
See here for the various options available:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Scroll down to section 5.

Again, if you want to edit the menu you need to do it in /etc/default/grub

---

