---
title: "D-Link DWL-G122 rev. B in Ubuntu, Possible? :S"
date: 2006-02-12
forum: General Help
---

### Post by pmh on 2006-02-12
Hello all...

I have some problem with my D-Link DWL-G122 (Wireless USB Stick), It seems to be installed, according to the "device manager" anyway. I don't have any connection, when I look in the "devive manager" it recognices that the usb stick is plugged in but when i open the "network config" tool it only displays "eth0" and "ppp0" there is no "wlan0" or anything like that.
So after a while I gave up and decided to use ndiswrapper, I used the command:

[FONT="Courier New"]sudo apt-get ndiswrapper-utils[/FONT]

and it where installed whitout any problems, then i installed the driver using the command:

[FONT="Courier New"]ndiswrapper -i Driver.inf[/FONT]

Checked if it where installed correctly using:

[FONT="Courier New"]ndiswrapper -l[/FONT]

then I used the command:

[FONT="Courier New"]sudo ndiswrapper -m
sudo depmod -a[/FONT]

and so far everything seemed to work, but when I type:

[FONT="Courier New"]sudo modprobe ndiswrapper[/FONT]

Nothing happens :( 

What am I doing wrong? :-? 

Any help is appriciated :-D

---

