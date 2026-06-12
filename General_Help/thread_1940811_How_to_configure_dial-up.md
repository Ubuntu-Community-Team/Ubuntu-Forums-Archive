---
title: "How to configure dial-up"
date: 2012-03-14
forum: General Help
---

### Post by KPKPW on 2012-03-14
I am a newbe to Linux. I need help with my "refurbished IBM ThinkCentre M50 Desktop w/installed 56k/modem (dial-up) w/Linux Ubuntu installed". I know "Windows"? I know there is a configuretion window for dial-up and how to do it but, not for Linux. Can someone help or send a manual of less than 30mbs? I would be great-full for any help.   Bob

---

### Post by raja.genupula on 2012-03-14
[http://ubuntuforums.org/showthread.php?t=1940294](http://ubuntuforums.org/showthread.php?t=1940294)

---

### Post by jerrrys on 2012-03-14
I do not use dial up, but this may help

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dial+up&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dial+up&sa=Search&cof=FORID:9)

---

### Post by grahammechanical on 2012-03-14
It is helpful if you tell us what version of Ubuntu you are using and what User Interface. Otherwise advice can be confusing as it does not relate to what you are seeing on your screen.

You could try using Gnome PPP. you install it through the Ubuntu Software Centre.

This link might help but some of the pictures are for earlier version of Ubuntu and not applicable to the latest Ubuntu.

[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

You should already have something called pppconfig installed by default. You run this utility from the command line.

Open a terminal and enter

```
sudo pppconfig
```

You will be required to enter your password. Do not expect anything to appear on the screen as you type your password (security reasons) but just press enter after you have type it in.

You will get a text style user interface. Gnome PPP gives you a graphical user interface to the same utility.

Regards.

---

### Post by KPKPW on 2012-03-15
On open/start I see "UBUNTU, with LINUX 3.0.0-16-generic" or "UBUNTU, with LINUX 3.0.0-16-generic (recovery mode)" or "Memory test (memtest86+)" or "Memory test (memtest86+, serial console 115200). At bottom of screen I read, "Use up or down arrows to..........Press enter to boot selected OS, 'e' to edit the commands before booting or 'c' for a command-line."
I am booting 1st entry. Also at the very top of page it says "GNU GRUB  version 1.99-12ubuntu5".
OS is UBUNTU 11.10...........I see #1...GNOME PPP (Not installed).  #2.... GNOME PPPon( Not installed).  #3...Network(network-manager-gnome) (Installed but no help as I only have dial-up)     User Interface?  User?     I think I need "GNOME PPP" but do not know where to get it or if I put it on a UBS flash drive how to then install it? Do I get a command line at boot up?
I am down loading a Ubuntu 10.10 manual as I write this, may be help full.   Open a terminal? Got no idea?  As for "you can go to System&#8212;>Administration &#8212;>Networking", the best I can do is click on "Icon" top right of screen = system settings to shut down?  I hope I have given you enough info..Some of Ubuntu acts like Windows but won't let me get to the heart of the system (maybe a good thing now).   Thank You......Bob

---

