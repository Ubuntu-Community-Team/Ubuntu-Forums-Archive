---
title: "Problems to install ubuntu 11.10 - Acer One ZA3"
date: 2011-10-29
forum: General Help
---

### Post by ribazzzz on 2011-10-29
Hi everyone :-)

I'm trying to install the Ubuntu 11.10 in my notebook Acer One ZA3.
Unfortunatly the gui doesn't start as i expected.Only appears the commnand line :-( . Someone has any idea how to resolve this problem....



Thks for your help...

---

### Post by dino99 on 2011-10-29
here is a standard config installation:

first you need to choose a good formatting tool: [http://partedmagic.com/](http://partedmagic.com/), install it on cd or usb stick, its a nice tool in case of trouble in future.

usually Ubuntu is installed that way :

- prepare partitions with external prog (partedmagic)
- built 3 partitions:
1) / which is the main one (root), need to be bootable and is ext3 or ext4 formated with about 10/12 gb
2) swap: about twice the real ram but max 2 gb (4 gb if suspend/hibernation is used)
3) /home which is your data partition: as much gb that you need

- download the "alternate" image and install it on usb ( unetbootin) if you are able to boot on usb, or burn it on cd (4x max speed). the "alternate" let you customize your installation, so as you have previously prepared your partitions and noted their names (/dev/sda or so), its easier to make a safe installation and place grub, when asked, on the / mbr partition.

---

### Post by ribazzzz on 2011-10-29
Thanks for your help... but unfortunatly i'm an absolute newbee  ... Anyone has "easy" solution for me??? A wizard like solution ?

---

### Post by Sef on 2011-10-29
What version of Ubuntu 11.10 did you install: desktop or server?

---

### Post by ribazzzz on 2011-10-29
I think that would be the desktop. I've just followed the instrutions of the download windows installer...

Many thanks..... :-)
[B]
[/B]

---

### Post by ribazzzz on 2011-10-30
Hi guys..

Any clue to resolve my problem ?

Thks

---

### Post by kmwjr1 on 2011-12-13
> **ribazzzz said:**
> Hi guys..

Any clue to resolve my problem ?

Thks



I have the Acer One ZA3, and the same problem.  I got the command line. Audio and video failed.  I resolved it by taking the hard drive out and hooking it to my desktop, and installed Ubuntu from there.  After it finished installation I then moved the drive back to the laptop.  It worked fine, and am using it to type this message.  I hope this message helped you.

The only problem that I'am currently having is that I can't get the right video driver.  I'm also new to Linux, so maybe that's why I'm having problems.

---

### Post by bodhi.zazen on 2011-12-13
I think this is the infamous GMA500

11.10 is not easy to get working, but 12.04 (Alpha) works well.

Download the alpha iso

[http://cdimage.ubuntu.com/releases/precise/alpha-1/](http://cdimage.ubuntu.com/releases/precise/alpha-1/)

When you boot, from CD or usb, at the boot menu, add the following options to the boot parameter

```
poulsbo.blacklist=yes console=tty1
```

You can add those options to /etc/default/grub, on the ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash poulsbo.blacklist=yes console=tty1"
```

---

