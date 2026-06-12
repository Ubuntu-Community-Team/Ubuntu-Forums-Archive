---
title: "Grub installed to wrong disk"
date: 2011-05-27
forum: General Help
---

### Post by buddyd16 on 2011-05-27
Well I messed up and would appreciate any help anybody can provide

**The back story:**
how my system was set up 2 data drives and 1 os drive split between vista and ubuntu. After a interior dusting of the case I plugged the drives into different sata cables switching my os drive from sda to sdb which I didn't notice until after I chose to install 11.04 over my current 10.04 install which by default seems to install grub to sda.

**The current problem:**
I have wiped ubuntu off its partition on the os drive and restored the mbr of the os drive using my vista cd but the data drive that was at sda during the ubuntu 11.04 install still has grub on it and every time I need to restart my computer I need to have the vista cd inserted and set the cd drive as the boot device to bypass grub and get into windows.

**The question:**
How do I go about removing grub from the data disc? 

I have everything important backed up from both the ubuntu and windows sides of the os drive as well as both data drives mirrored to their own separate backup drives so having to do a full wipe is not a problem was just wondering if it is easier than that though.

thanks for any help

---

### Post by LordNeo on 2011-05-27
So, the sdb is Windows HD and sda is Ubuntu HD?
You wiped the grub from sdb, but grub on sda is still annoying you?

The easiest way (if you want to keep playing with Ubuntu) would be to update grub and use it as boot loader for both OS.

If you want to remove it from both drives i would suggest first to switch (in the BIOS) the boot order, so it will read the Windows Loader in sdb first and never get into grub in sda.

For real remove, you can unplug sdb and boot with the Vista CD and then "repair" (fixmbr, wich actually only install Windows Loader) on sda.

---

### Post by buddyd16 on 2011-05-27
LordNeo: Actually both ubuntu and vista were on SDB just separate partitions

so the setup before the the 11.04 install was:
```
sda --> data disk 1
sdb (grub)
 sdb1 vista
 sdb2 ubuntu
sdc --> data disk 2

```

after the 11.04 install:
```
sda (11.04 grub) --> data disk 1
sdb (old grub)
 sdb1 vista
 sdb2 ubuntu 11.04
sdc --> data disk 2

```

Current:
```

sda (11.04 grub) --> data disk 1
sdb windows boot loader
 sdb1 vista
 sdb2 empty partition
sdc --> data disk 2

```

hopefully that will help clear up some confusion.

Whatever the solution may be I intend on installing Ubuntu again but need to keep vista in the loop as well for some light gaming with old college friends

---

### Post by LordNeo on 2011-05-27
Well, like i said before, if you want to keep Ubuntu, then boot in ubuntu and then open a terminal and type:

sudo update-grub

Once finished, reboot and you will find grub being able to boot from Ubuntu in sda and Windows Vista in sdb.

If you don't want to boot in Ubuntu for a while, go to your BIOS and change the boot order to sdb then sda (you will find it ordered by HD brand-name, just invert the current setup), that should be more than enought to trigger windows loader without getting grub ever without having to swap cables or whatever else.

---

### Post by buddyd16 on 2011-05-27
Is there a way to move grub to sdb so it resides on the same disk as the ubuntu install?

---

### Post by LordNeo on 2011-05-27
You can do:

sudo grub-install --recheck /dev/sdb

That will install grub in sdb (but according to your previous post, you have Ubuntu in sda :S)

I'm not sure if this will remove the current grub detected (in whatever disk it is), most surely will only check if /dev/sdx has grub and if not, will install it and do the necesary magic to use it.

PD: From your chart, doing this will replace the Windows Loader and you will only have GRUB managing both OS. If you plan to remove the drives and have: sda = Ubuntu Only, sdb = Windows Only, i suggest to install GRUB on sda and Windows Loader in sdb, so GRUB will be able to boot to Ubuntu and Windows and if you happen to remove that disk you will still have Windows Loader to boot your Windows Vista.

Best regards

---

### Post by buddyd16 on 2011-05-27
LordNeo: ah see we have a disconnect both windows and ubuntu are on sdb but grub is on sda which is where ubuntu 11.04 installs it by default.

thanks for the info I'll look into how the recheck option works.

---

### Post by LordNeo on 2011-05-27
Well, if both systems are on sdb, then just do:

sudo grub-install --recheck /dev/sdb

and then:

sudo update-grub

That should make everything run smoothly.

If grub on /dev/sda is still making noise, disconnect /dev/sdb and use WinCD+sda to delete the mbr from there (or just format the entire disk if possible).

PD: I just found this: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) look at point 16

---

