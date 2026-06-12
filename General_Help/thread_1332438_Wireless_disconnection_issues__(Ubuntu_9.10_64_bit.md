---
title: "Wireless disconnection issues  (Ubuntu 9.10 64 bit + Acer laptop)"
date: 2009-11-20
forum: General Help
---

### Post by shobhitg on 2009-11-20
Hi,

I installed Ubuntu 9.10 (dual boot with win 7) on my new Acer laptop.

In Ubuntu, for some reason my wireless disconnects randomly. Once disconnected I can't get it running again, unless I reboot Ubuntu.

I had been searching and browsing this forum for solutions, and I tried following some instructions to install something called madwifi (can't find that thread now). Anyway, that didn't solve my problem.

Because of this problem, I am starting to have the tendency to boot up in windows.

I would greatly appreciate if you guys can help me identify and solve this problem.

To begin with; Any ideas on what I can try to reproduce the issue (eliminating the randomness).

Let me know what info I can provide here (also tell me the commands to find that info).

regards,
Shobhit

---

### Post by P4man on 2009-11-20
lets start by finding out which exact wifi card you have. Open a terminal and type

```
lspci
```

and possibly

```
lsusb
```

copy paste the output here.

---

### Post by shobhitg on 2009-11-20
sudo lspci > lspci.txt
sudo lspci -v > lspci_verbose.txt
sudo lsusb > lsusb.txt

Output files attached.

---

### Post by P4man on 2009-11-20
Have a look at this bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/426130](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/426130)

its the same wifi card as you:  Atheros-AR928X

Suggested workaround is installing wicd. Could be worth a shot.

---

### Post by hal10000 on 2009-11-20
I can confirm that installing wicd makes wireless networking a lot more comfortable.

---

### Post by shobhitg on 2009-11-20
Thanks for telling me that in such clear language.

I have installed Wicd Network Manager, but my original network manager erred out and its icon dissapeared from the top bar. I have no way to continuously know the signal strength.

The reason I am concerned about this is because when I open Wicd and refresh; it shows my network at 7%. And there are at least a few more networks from nearby apartments which have higher strength than mine. 


Since the issue was random, now only time will tell if it disconnects or not. I will update about this in a couple of days.



*Is there a name for that top bar in Ubuntu? (like in windows the bottom bar is called Task Bar).

---

### Post by P4man on 2009-11-20
> **shobhitg said:**
> Thanks for telling me that in such clear language.

I have installed Wicd Network Manager, but my original network manager erred out and its icon dissapeared from the top bar. I have no way to continuously know the signal strength.

Restart X (or reboot). Upon installing wicd the original network manager gets uninstalled. You cant have both. 
> 
The reason I am concerned about this is because when I open Wicd and refresh; it shows my network at 7%. And there are at least a few more networks from nearby apartments which have higher strength than mine. 


Heh. Well, try setting a different channel on your access point ?

> 
*Is there a name for that top bar in Ubuntu? (like in windows the bottom bar is called Task Bar).

The top and bottom thingies are called "panels". The area in which you see the volume and network manager is the notification area.

---

