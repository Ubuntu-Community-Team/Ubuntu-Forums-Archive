---
title: "Total Grub newbie"
date: 2010-02-11
forum: General Help
---

### Post by ScarletSpider85 on 2010-02-11
Hi all,

I'm very new to the world of Ubuntu, which is currently sharing space on my system with Windows 7, which I still currently require to run most of my games and other appllications.

I'm using Grub as the bootloader, I'm told it's possible to configure Grub to boot an OS of the user's choice, with a preset time delay.

I've seen a thread or two here on how to do this, but they mention a Grub folder, which I cannot find anywhere on either OS, on any of the hard drives on my PC.

As (at least for the time being) I still need to use Windows as my primary OS, please could someone let me know how I can find this folder, so I can work from there?

Thanks muchly. :)

---

### Post by flippo on 2010-02-11
If your running ubuntu 9.04 or earlier:

the grub folder is in /boot/ you'll have to do your editing as root, so type something like ```
gksu gedit /boot/grub/menu.lst
``` in a terminal to get started.  As far as actually configuring it, thats another story.  Just post if you need any help.

---

### Post by audiomick on 2010-02-11
Hi.
If your Ubuntu is a fresh install of Karmic 9.10, you will have grub 2. Info on that here
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

If it is an older Ubuntu, 9.04 or earlier, or 9.10 updated from an earlier, it will be grub legacy:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

