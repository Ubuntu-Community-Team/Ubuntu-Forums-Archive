---
title: "How do I log on to Windows XP Home Edition?"
date: 2006-03-16
forum: General Help
---

### Post by youBun2 on 2006-03-16
Alright, I am in the same boat as you all but far worse.

I currently run Windows XP Home Edition on my desktop that was bought last February. The file system on my main and only hard drive of 200 GB is NTFS.

Yesterday a friend gave me a copy of Ubuntu (official copy from the website) and I decided to load up the Live CD. Without a result I found that perhaps it is just the Live CD and so I went ahead and started with an installation.

Using a partioning program I managed to create a 10 GB partition for Linux etc. I carried on with the install and towards the end it asked me if I wanted to have the GNU GRUB installed on my C: (with Windows XP) as to have a choice in OS when at boot-up.

Innocent me went ahead with that choice and enjoyed the first few steps at seeing Ubuntu. I managed to create myself a user account and I logged in... it froze. I then decided to restart and load up Windows XP instead. It won't load. When I select Windows XP Home Edition it has:

root (hd0,1)
savedefault
makeactive
chainloader +1

and stops. When I checked out the same boot-up process for Ubuntu, I saw that it reads:

root hd(0,2)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/sda3 ro quiet splash
intrid /boot/initrd.img-2.6.12-9-386
savedefault
boot

and obviously loads Ubuntu and allows me to log in but freezes on the centered image.

From what I can see, it appears Windows XP doesn't load up its kernal or something like that. Are there any ways I can simply log on to my Windows system?

---

### Post by aysiu on 2006-03-16
It sounds as if both your installer CD and live CD were corrupt.

If you get a good Ubuntu CD, you can reinstall and everything should be fine.

---

### Post by Ramses de Norre on 2006-03-16
To solve your ubuntu problem:
[http://www.ubuntuforums.org/showpost.php?p=783606&postcount=2]("http://www.ubuntuforums.org/showpost.php?p=783606&postcount=2")
This driver will let you login, though do a search for the fglrx driver then for better performance.

---

### Post by youBun2 on 2006-03-16
I will try that driver. But my keyboard does not respond when I log in. Is this BEFORE I log in to Ubuntu?

---

### Post by Ramses de Norre on 2006-03-16
Do ctrl+alt+F1 as soon as possible after the splash screen, before everything freezes in graphical mode.

---

### Post by youBun2 on 2006-03-16
Alright, that works now and Ubuntu is loaded. What is my next step to enabling Windows XP to boot up?

---

### Post by bender unit on 2006-03-16
[QUOTE=youBun2]Alright, that works now and Ubuntu is loaded. What is my next step to enabling Windows XP to boot up?[/QUOTE]

Have you tried booting the rescue mode with a Windows XP installation CD? That you give you a command line where you can do something like

```
fdisk /mbr
```

Which should restore your original (Windows) MBR, i.e. the normal Windows boot loader. Of course, it will destroy GRUB, leaving you no way to boot your Ubuntu again (other than reinstalling it).

---

### Post by redboar on 2006-03-16
As far as I know, all copies of Windows XP use the Recovery Console, which is an option chosen at the beginning of the install process.  He would then issue the command[HTML]fixmbr[/HTML] then reboot and it would allow him to log back onto Windows.  Of course, GRUB would be removed and he'd have to reinstall Ubuntu which it sounds like he has to do anyways.

This is the case for XP Professional, but I'm not sure about XP Home.  I'd recommend XP Pro over Home for any user.

---

### Post by markiss on 2006-03-27
There is a fixmbr command in the windows xp home recovery console. If I'm not mistaken you can reinstall grub from the live CD. If you are in ubuntu you can reinstall grub. I would try a third party boot loader. I've had good luck with a shareware version of OSL2000. It might just recognize your linux partition and boot from it.

For the record. The only difference between winXP home and Pro is advanced networking capabilities. Unless you are setting up an extensive office network there is no need for Pro. The instalation files alone are about 250 megs extra space, why bother? 

Markiss

---

### Post by Video Toaster on 2006-03-27
[QUOTE=markiss]There is a fixmbr command in the windows xp home recovery console. If I'm not mistaken you can reinstall grub from the live CD. If you are in ubuntu you can reinstall grub. I would try a third party boot loader. I've had good luck with a shareware version of OSL2000. It might just recognize your linux partition and boot from it.

For the record. The only difference between winXP home and Pro is advanced networking capabilities. Unless you are setting up an extensive office network there is no need for Pro. The instalation files alone are about 250 megs extra space, why bother? 

Markiss[/QUOTE]

There are other little differences, such as the ability to log on using the built-in "Administrator" account in normal mode by pressing CTRL+ALT+DEL twice (to get to the Win2K logon screen) and logging on.  In XP Home you have to start in Safe Mode to use the built-in "Administrator" account.

There's more stuff, but I'm too tired to think of any of it. :D

---

### Post by BlaineM on 2006-03-27
This is not meant as hatred... but there are a lot of different and very powerful tools and utilities in XP pro that aren't in Home.  But yes, if you are just using it at home to surf the internet and type things and download stuff, home is the way to go for the average consumer, in the Windows world anyway.  It costs less too, but comes with a ton of crap (internet offers and junk in my opinion things that I delete)  Anyways, I am moving to Linux more and more as the days go by, and I get it working better (wireless, and touchpad problems).  It costs me nothing but time and Way more customizable... :-D

---

