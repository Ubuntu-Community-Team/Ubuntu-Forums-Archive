---
title: "Help ubuntu will not load!"
date: 2009-09-21
forum: General Help
---

### Post by AvatarFACE on 2009-09-21
I am runing ubuntu 7.04.

I adjusted a setting in the "login screen" in "settings" I can't remember what it was but it was supposed to enable something and now when I turn it on it sits on a blank screen with the cursor stuck in the loading circle, I have left It for hours and it will not go to the logon screen. I tried booting to the OS disk and that worked but I do not know how to change the settings for my user when booted to the CD. I also tried booting in "recovery mode" and that was no help, I got the same result.
I am a bit of a noob with linux and do not know any command line stuff.

Help me please!

---

### Post by AvatarFACE on 2009-09-22
I have tried alt ctrl 1-12 and nothing helps, I can get int command line interface using those shortcuts but I do not know what I changed or how to change any settings through the terminal. Is there a way to force a GUI login through the terminal? I can login through the terminal but it stays in the command line.

---

### Post by badger_fruit on 2009-09-22
> **AvatarFACE said:**
> I have tried alt ctrl 1-12 and nothing helps, I can get int command line interface using those shortcuts but I do not know what I changed or how to change any settings through the terminal. Is there a way to force a GUI login through the terminal? I can login through the terminal but it stays in the command line.


Try logging in at the console and use the commands

```

sudo init 3
sudo init 5

```if that doesn't work, I believe that there's a "safe mode" option when you reboot ```
sudo reboot
``` which will allow you to get into the GUI.

---

### Post by P4man on 2009-09-22
open a tty using control alt F1. Then try this command:

```
sudo dpkg-reconfigure gdm
```

after that, you can try logging in to gdm again with:

```
sudo /etc/init.d/gdm restart
```

(or reboot if you prefer)

---

### Post by AvatarFACE on 2009-09-22
also during the command line it comes up with "bcm43xx: error: microcode "bcm43xx_microcode5.fw" not available or load failed" I have googled this and I do not have a wireless card like the  people in those articles had, but through some comments from those articles a user said that it should not cause a problem like I have. I do have a TV card in the computer but that has been successfully installed for years.

---

### Post by AvatarFACE on 2009-09-22
> **P4man said:**
> open a tty using control alt F1. Then try this command:

```
sudo dpkg-reconfigure gdm
```

after that, you can try logging in to gdm again with:

```
sudo /etc/init.d/gdm restart
```

(or reboot if you prefer)

I just tried this and nothing changed, i used the code and re-booted.

---

### Post by P4man on 2009-09-22
then try this (still from tty):

```
sudo mv  /etc/gdm/gdm.conf-custom  /etc/gdm/gdm.conf-custom.backup
sudo reboot 
```

---

### Post by AvatarFACE on 2009-09-22
after the fisrt line it says "mv:missing destination file operand after '/etc/gdm/gdm.conf-custom.backup' Try 'mv --help' for more information" (dont worry i see I have just typed it in wrong)

---

### Post by AvatarFACE on 2009-09-22
typed it in successfully and rebooted and I can now login. 
[SIZE="6"]Thank you heaps! [/SIZE]

---

