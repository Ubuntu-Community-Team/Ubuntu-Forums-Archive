---
title: "Ubuntu won't start up anymore"
date: 2011-01-17
forum: General Help
---

### Post by t36 on 2011-01-17
Hi,

I have this major problem with the latest version of Ubuntu (10.10). Since I applied this automatic update Ubuntu won't startup anymore.

I am 99% sure it's something to do with the graphics drivers. I have an ATI Radeon HD5850. I can still boot up in safe mode in one of the older kernels of Ubuntu. But with the latest kernel I can't even get into safe mode.
What I want to do now, is to remove all traces of any potential drivers and then reinstall them. What is the best way to do this?

And by clean, I mean really really clean.

Thanks in advance,

t36

---

### Post by Rubi1200 on 2011-01-17
Are you able to boot into Recovery Mode for the kernel in question?

If so, drop to a command terminal and run these commands:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure -phigh xserver-xorg
```

If this doesn't help, try an older kernel and reconfigure the drivers.

---

### Post by marin123 on 2011-01-17
its xorg problem, you have to reinstall video drivers. can you boot into failsafe? if you cant, try booting into single mode, thats how i did it.

---

### Post by t36 on 2011-01-17
> **Rubi1200 said:**
> Are you able to boot into Recovery Mode for the kernel in question?

If so, drop to a command terminal and run these commands:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure -phigh xserver-xorg
```

If this doesn't help, try an older kernel and reconfigure the drivers.

First of all thanks for the replies. 

I can still boot into failsafe graphics mode. When I try to rename the xorg-conf I get a message that this file does not exist.

Then I ran the second command and nothing seemed to happen.

I tried to look for drivers via the "additional drivers" menu, but none appear.

Maybe not important but, since the problem, GRUB doesn't count down anymore. Not big deal, but strange nonetheless.

What is now the best course of action?

---

### Post by wilee-nilee on 2011-01-17
Just hit the submit reply button once it will post the forum is running slow.

---

### Post by ajgreeny on 2011-01-17
I don't know if this was a typo, but it's not **xorg-conf**, but **xorg.conf**.  If you tried with the dash instead of the . try again with correct name.

---

### Post by marin123 on 2011-01-17
```
sudo apt-get install --reinstall xserver-common xserver-xorg
```

that should reinstall the drivers...

---

### Post by t36 on 2011-01-17
I copy pasted the command involving the xorg.conf so there is no typo there.

sudo apt-get install --reinstall xserver-common xserver-xorg does not seem to help, there still no drivers to select from in the "Additional Drivers" menu.

Anything else I can try?

Ps. Let's hope I don't get the multi-post thing again :)

---

### Post by marin123 on 2011-01-18
--reinstall command reinstalls graphic drivers, you will not get entry in additional drivers menu.

did you maybe install drivers that you downloaded from amd website?

---

### Post by t36 on 2011-01-18
> **marin123 said:**
> --reinstall command reinstalls graphic drivers, you will not get entry in additional drivers menu.

did you maybe install drivers that you downloaded from amd website?

I experimented with some drivers in the past. Is that a problem?

---

### Post by t36 on 2011-01-18
Hmm, I tried reinstalling the drivers released by ATI and now everything works again. Still curious that things just stopped working. Oh well.

---

### Post by marin123 on 2011-01-18
similar thing happened to me. i had installed ati drivers from their website (they are newer then ones in additional drivers) and later installed Xorg update. that messed up everything. after reinstalling drivers from ati i got my ubuntu back :)

---

