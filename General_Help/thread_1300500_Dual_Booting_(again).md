---
title: "Dual Booting (again)"
date: 2009-10-25
forum: General Help
---

### Post by Kilroth on 2009-10-25
OK, With other versions of Ubuntu it was easy to dual boot with two hard drives each having there own OS. But now I am just confused with 9.10, it has grub-2 as I understand it. I like to do things manually, so what I used to do is I used Thunar and went to Boot>Grub>Menu.lst and i knew what to do from there but in 9.10 there is no Menu.lst so How do I do it please Help thank you   

I have a 

500GB Hard drive (SATA) with Ubuntu 9.10 

80GB Hard drive with Windows Vista

---

### Post by Herman on 2009-10-25
GRUB 2 has grub.cfg instead of menu.lst.
We're not supposed to edit our grub.cfg files ourselves.
A big improvement with GRUB 2 is its ability to scan your computer and detect other operating systems and automatically add them to grub.cfg 
Here's the command I use to get GRUB 2 to scan my computer and make a new grub.cfg file,
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```
Just type that command, press 'enter', type your password and sit back while GRUB 2 does all it's own editing work. :P

---

### Post by Herman on 2009-10-25
GRUB 2 will be a lot easier for new users than the old GRUB, there will be programs for modifying and customizing your GRUB menu the way you like, say for example adding a splashimage or changing the boot order and so on. SUM (Start Up Manager) seems to be the most popular program for editing GRUB 2 so far. 
[StartUp Manager]("https://help.ubuntu.com/community/StartUpManager") - Ubuntu Community Docs 
[StartUp Manager – change settings in Grub, Grub2 and Usplash]("http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html") - UbuntuGeek

---

### Post by Herman on 2009-10-25
Both GRUB 2 itself and Start Up Manager are still works in progress and at the moment there may be some tricks that we're used to being able to do with GRUB that GRUB2 and SUM might not have available yet or at least aren't as easy for the time being.
That will mean if you really want to do some of the things we did in GRUB Legacy, maybe like adding a splashimage or something like that, we still need to resort to editing files by hand (with a text editor).

But remember, we're not supposed to edit our grub.cfg ourselves directly.

Instead, there are some files that the mkgrub.cfg program looks at when it automatically makes us a new grub.cfg file which we can edit manually if we like to make any changes we want in our GRUB 2 menus. 
One such file is /etc/default/grub, and other files are the files in /etc/grub.d which begin with numbers like '00_header  05_debian_theme  10_linux  20_memtest86+  30_os-prober  and 40_custom'.
Editing those files and then running 'sudo grub-mkconfig -o /boot/grub/grub.cfg' will be the only way to make GRUB 2 do some of the things we're used to being able to do with GRUB for now, until SUM has more features available.

---

### Post by Kilroth on 2009-10-25
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sdb1
[COLOR="Red"]grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.[/COLOR]



Is this ok because I do not know what the error is can someone please tell me

---

