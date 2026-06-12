---
title: "Really need help with wireless"
date: 2011-11-26
forum: General Help
---

### Post by Deery50 on 2011-11-26
on my computer which was a vista but I installed ubuntu 11.10 on it. I installed STA drivers and wireless was working until i restarted. After I restarted it was almost like wireless didn't even exist. Please help! I will reply with some additional information in a second, I am just bringing my other computer downstairs and getting my other computer hardwired.

---

### Post by Deery50 on 2011-11-26
Ok here is some additional information.
Upon entering command: 
```
lspci -vvnn | grep 14e4
```

I get this as result:

```
01:05.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

```

That means:

Card/Model - BCM4318
PCI-ID - [14e4:4318]

---

### Post by Deery50 on 2011-11-26
This is probably a stupid mistake but i was following an online tutorial and I got stuck at this:
Step 2.

> Under the desktop menu System > Administration > Hardware/Additional Drivers, the b43 drivers can be activated for use.

Note: A computer restart may be required before using the wifi card.

LiveCD/LiveUSB

Where and what is the desktop menu? Is there one for ubuntu 11.10?

---

### Post by cwwilson721 on 2011-11-26
I'm assuming you are using Unity. Saying "Ubuntu" means diddly. Ubuntu (the Distro) can run with any number of Desktops: Gnome, Gnome 3, BlackBox, KDE, LXE, etc, etc...

In Unity, in the upper right corner, click your name, then scroll down to System Settings. In there, open Additional Drivers

---

### Post by Deery50 on 2011-11-26
Thanks for your reply. The driver I am looking for isn't on that list. However I know I have it because when I use the command
```
sudo modprobe b43
``` in terminal my wireless is enabled for temporary use but I don't want to have to enter than every time I launch the computer

---

### Post by cwwilson721 on 2011-11-26
Go to that same list, and make sure the STA driver is disabled.

then, in terminal, type:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -r b43 ssb
sudo modprobe b43
```

If you get an error on the second step about "no such" or something, you can ignore it.

After those steps, in terminal again, type```
lsmod | grep b43
```

That should tell you it's loaded.

You might have to reboot to actually use it

---

