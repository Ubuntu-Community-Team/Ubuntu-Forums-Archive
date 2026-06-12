---
title: "XUBUNTU 12.04 Startup Manager?"
date: 2012-05-18
forum: General Help
---

### Post by Jerry N on 2012-05-18
Is there an equivalent in XUBUNTU 12.04 to **Startupmanager** which provides for selecting the default OS in a multiboot environment?  It does not seem to be in the normal repositories.  

Jerry

---

### Post by holycow131415 on 2012-05-18
i think you are talking about grub before it boots into xubuntu.

edit the /boot/grub/menu.lst to your needs. < for grub, not grub 2. grub 2 starts at version 1.99 i believe.

for grub 2 edit /boot/grub/grub.cfg

[https://wiki.archlinux.org/index.php/GRUB2#Manually_creating_grub.cfg](https://wiki.archlinux.org/index.php/GRUB2#Manually_creating_grub.cfg)

---

### Post by QIII on 2012-05-18
menu.lst does not exist any longer if you are using GRUB2.

Do not manually update anything.  Unless you know exactly what you are doing you can FUBAR things you wish you hadn't.

In the terminal

```
sudo update-grub
```or 

```
sudo update-grub2
```For further help, look here:

[[URL="https://help.ubuntu.com/community/Grub2[/URL"]Grub 2]("https://help.ubuntu.com/community/Grub2")[/url]

(Just as an aside, a former poster used the call Startup Manager "Startup Mangler".  I miss RanchHand.)

---

### Post by plucky on 2012-05-18
> **Jerry N said:**
> Is there an equivalent in XUBUNTU 12.04 to **Startupmanager** which provides for selecting the default OS in a multiboot environment?  It does not seem to be in the normal repositories.  

Jerry

Try [Grub Customizer](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

Follow the instructions to install the PPA and then the program.

Good Luck

---

### Post by Jerry N on 2012-05-18
No real problem here, I guess.  I had thought the 12.04 version of Xubuntu would be to my liking but I also installed Mint 13 (RC) with the MATE desktop and it seems to be much friendlier and quite a lot faster than Xubuntu 12.04.  

Jerry

---

