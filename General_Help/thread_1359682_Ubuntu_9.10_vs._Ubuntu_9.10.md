---
title: "Ubuntu 9.10 vs. Ubuntu 9.10?"
date: 2009-12-20
forum: General Help
---

### Post by iSephy on 2009-12-20
I have a few questions...


[LIST=1]
[*]Does Ubuntu 9.04 use GRUB Legacy?
[*]Is there a way to get either to use some sort of a Windows Device Manager knock-off?
[*]Can I install GRUB Legacy on Ubuntu 9.10 easily? If so, how?
[/LIST]

Thanks

~Seph:guitar:

---

### Post by shaon3343 on 2009-12-20
[B]yes ubuntu 9.04 use GRUB legacy. You can install GRUB legacy in your ubuntu 9.10 and for that you should check this:
[http://ubuntuforums.org/showthread.php?p=8401165#post8401165](http://ubuntuforums.org/showthread.php?p=8401165#post8401165)[/B]

---

### Post by 3rdalbum on 2009-12-20
> **iSephy said:**
> I have a few questions...


[LIST=1]
[*]Does Ubuntu 9.04 use GRUB Legacy?
[*]Is there a way to get either to use some sort of a Windows Device Manager knock-off?
[*]Can I install GRUB Legacy on Ubuntu 9.10 easily? If so, how?
[/LIST]

Thanks

~Seph:guitar:

1. Yes, unless you select Ext4 as your main filesystem
2. Well yeah; but you don't really need it because of the "lspci", "lsusb" and "lshw" commands. Hardinfo is basically a GUI for those.
3. Not sure - why do you want to?

---

### Post by iSephy on 2009-12-20
I want to so I can use a tutorial for something which involves using the menu.lst file which is not in GRUB2.

---

### Post by iSephy on 2009-12-20
Also, the reason I want the device manager knock-off is because I need to install some drivers for my Graphics Card, PCI Wireless Adapter, Ethernet Controller, and Sound Card.

---

### Post by 3rdalbum on 2009-12-20
> **iSephy said:**
> Also, the reason I want the device manager knock-off is because I need to install some drivers for my Graphics Card, PCI Wireless Adapter, Ethernet Controller, and Sound Card.

Most of those things should be working out-of-the-box.

Hardinfo is not going to be any more help to you than the "lspci" command. It will tell you what the devices are and hopefully what chipsets they use so you can use Google to find a driver. But usually drivers for these things should be preinstalled. I'm not sure how you're going to install Hardinfo either if you don't have Ethernet or Wifi.

---

### Post by iSephy on 2009-12-20
I have an ethernet cable, but I need to install these devices to get internet and play an MMORPG.

---

### Post by iSephy on 2009-12-20
Also, I have no idea what lspci, lsusb, or lshw mean... >_<

---

### Post by slakkie on 2009-12-20
All Ubuntu releases prior to Karmic support and install grub-legacy, including 9.04.

Karmic (9.10) can use grub-legacy. Just do an upgrade from 9.04 and it will NOT replace grub-legacy with grub2. Only fresh installs of 9.10 get grub2 for free.

Device manager tools are available, don't know the GUI ones, but the cli tools have been mentioned in this thread.

---

### Post by efflandt on 2009-12-20
> **iSephy said:**
> Also, I have no idea what lspci, lsusb, or lshw mean... >_<

Those are commands you can run in a terminal or console (text).  For example "**ls**" is a common command (like "dir" in msdos) for listing directories and files, and similarly **lspci** lists pci devices, **lsusb** lists usb devices.  I was not aware of **lshw**, but that apparently lists info about hardware.

You should also become familiar with the "**man**" command (short for manual) to see what commands do and command options, and "apropos" to look for any command that refers to a particular term if you do not know what you are looking for.

```
efflandt@efflandt64-desktop:~$ apropos hardware
arch (1)             - print machine hardware name (same as uname -m)
clock (8)            - query and set the hardware clock (RTC)
hwclock (8)          - query and set the hardware clock (RTC)
lshw (1)             - list hardware
toshset (1)          - manipulate bios and hardware settings of Toshiba laptops
vbetool (1)          - run real-mode video BIOS code to alter hardware state
efflandt@efflandt64-desktop:~$ apropos pci
lspci (8)            - list all PCI devices
pcilib (7)           - a library for accessing PCI devices
pcimodules (8)       - List kernel driver modules available for all currently...
rpcinfo (8)          - report RPC information
setpci (8)           - configure PCI devices
update-pciids (8)    - download new version of the PCI ID list

```Then [COLOR=Red]man lspci[/COLOR] would tell you how to use the lspci command.  However, some commands you may need to prefix with sudo like [COLOR=Red]sudo lspci -v
[COLOR=black]
If you upgrade 9.04 to 9.10 it retains the old grub unless you change it.  If you install 9.10 from scratch it uses grub2.  That should not be an issue unless you also have a different Linux version installed that uses a different grub.  Unless you are already familiar with something from the past, why learn something old if you could learn how to use what is now and the future.

The most common things that "might" need special drivers are video and wireless.  But 9.10 will suggest what to use for proprietary devices.  If you install special drivers, they may not update automatically, and you are on your own maintaining them.
[/COLOR][/COLOR]

---

### Post by DeMus on 2009-12-20
> **3rdalbum said:**
> 1. Yes, unless you select Ext4 as your main filesystem

Where did you find that? I use 9.04 since April of this year on Ext4 with Grub 1 legacy. Why do you think this combination does not work? It works perfectly. Or should I say: it works? Grub 2 is a disaster and should never have been born. It's exactely the same mistake as MS made when they stopped using boot.ini and made some kind of complicated program to do exactly the same, with 1 difference: now it is much more complicated to get it fine tuned.
And still people dare to say: Linux is not Windows. Then why copy the bad things from Windows?

---

### Post by slakkie on 2009-12-20
You are aware that grub-legacy has NO active development or support. That is why we have grub2. And it ain't bad, it is new and people are not used to it yet.

---

### Post by bodhi.zazen on 2009-12-20
> **slakkie said:**
> You are aware that grub-legacy has NO active development or support. That is why we have grub2. And it ain't bad, it is new and people are not used to it yet.

+1

grub 2 is, IMO, far superior to grub-legacy, HOWEVER, it does require learning a few new tricks.

[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2") 

In general, grub 2 is as problem free as grub-legacy (yes, there are occasional problems), but not so much that I would call grub 2 inferior to grub1 or a disaster.

Moving forward we will almost certainly see graphical tools rolled out that will assist in managing grub2 without having to learn and edit config files (assuming of course you do not like that kind of thing).

---

### Post by iSephy on 2009-12-21
Fixed it all :D

---

