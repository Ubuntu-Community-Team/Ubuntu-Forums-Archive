---
title: "Ubuntu 11.10 No Desktop."
date: 2012-01-05
forum: General Help
---

### Post by keisko on 2012-01-05
Hello,

I've upgraded to Ubuntu v11.10.. Everything went ok during upgrade. Once I restart the computer, I don't get the desktop anymore. I See only a blackscreen with a few messages such as:
Starting bluetooth: [OK]
Starting webserver apache [OK]
Enabling xxxxxxx.. [OK]
etc..

I can login via SSH and Network.

How to I re-active, enable or install the desktop again? What happened?

---

### Post by 2F4U on 2012-01-05
What are your hardware specifications, what graphics card? You could try to add nomodeset to the grub kernel boot parameters and see if that helps.

---

### Post by topsites on 2012-01-05
You did remove the CD from the CD-Rom drive AND re-set the boot sequence in your BIOS to HDD 1st?

---

### Post by keisko on 2012-01-06
> **2F4U said:**
> What are your hardware specifications, what graphics card? You could try to add nomodeset to the grub kernel boot parameters and see if that helps.

It's a very old server computer. Pentium 4 2.8.. 512 Ram.. SuperServer 5013c-t

> **topsites said:**
> You did remove the CD from the CD-Rom drive AND re-set the boot sequence in your BIOS to HDD 1st?
There is no cd.


This is the link to my old server machine: [http://www.supermicro.com/products/system/1U/5013/SYS-5013C-T.cfm](http://www.supermicro.com/products/system/1U/5013/SYS-5013C-T.cfm)

---

### Post by Catharsis on 2012-01-06
> **2F4U said:**
> What are your hardware specifications, what graphics card? You could try to add nomodeset to the grub kernel boot parameters and see if that helps.

Seconded, both the graphics card and whether 'nomodeset' works.

It might just not be switching to VT7; try pressing Ctrl+Alt+F7.

You can try switching to another VT (i.e. Ctrl+Alt+F2), login, and run 'startx'.

---

### Post by keisko on 2012-01-06
I'm gonna try the command below
```
sudo aptitude install gnome-desktop-environment
```

---

### Post by keisko on 2012-01-06
> **Catharsis said:**
> Seconded, both the graphics card and whether 'nomodeset' works.

It might just not be switching to VT7; try pressing Ctrl+Alt+F7.

You can try switching to another VT (i.e. Ctrl+Alt+F2), login, and run 'startx'.

Once I use following command: sudo aptitude install gnome-desktop-environment
I saw your reply :)
I pressed on CTRL+Alt+f7 nothing happend.
And then I pressed CTRL+ALT+F2, logged and typed startx.. wohaaa I'm in.. Desktop come back lol.. thx man!

and thx everyone who tried to help me!

---

### Post by keisko on 2012-01-06
it looks like once I restart or reboot the machine, I must always do CTRL+ALT+F2.. log in.. startx.. is there easy way for this?

---

### Post by Catharsis on 2012-01-06
Looks like lightdm just isn't starting when your computer boots. See if reconfiguring it helps:
```
dpkg-reconfigure lightdm
```
If that doesn't work, just reinstall it:
```
sudo apt-get update && sudo apt-get install --reinstall lightdm
```

---

### Post by keisko on 2012-01-06
> **Catharsis said:**
> Looks like lightdm just isn't starting when your computer boots. See if reconfiguring it helps:
```
dpkg-reconfigure lightdm
```If that doesn't work, just reinstall it:
```
sudo apt-get update && sudo apt-get install --reinstall lightdm
```
I tested with both of those commands but doesn't help.. :(

---

