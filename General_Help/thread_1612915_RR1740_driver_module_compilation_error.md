---
title: "RR1740 driver module compilation error"
date: 2010-11-03
forum: General Help
---

### Post by AllGamer on 2010-11-03
running the latest ubuntu 10.10 desktop i386
i followed this guide for reference when building the updated drivers
[https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid)

all paths and references have been updated to reflect my version of the driver

**original error during compilation**:

DKMS make.log for rr174x-2.4 for kernel 2.6.35-22-generic (i686)
Wed Nov  3 01:28:03 EDT 2010
make: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
scripts/[COLOR=Red]Makefile.build:49: *** CFLAGS was changed in "/var/lib/dkms/rr174x/2.4/build/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.[/COLOR]
make: *** [_module_/var/lib/dkms/rr174x/2.4/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'



**to "force" it to work i used this work around**:

sudo KBUILD_NOPEDANTIC=1 make install

[sudo] password for USER: 
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /usr/src/rr174x-2.4/.build/os_linux.o
  CC [M]  /usr/src/rr174x-2.4/.build/osm_linux.o
  CC [M]  /usr/src/rr174x-2.4/.build/div64.o
  CC [M]  /usr/src/rr174x-2.4/.build/hptinfo.o
  CC [M]  /usr/src/rr174x-2.4/.build/config.o
  LD [M]  /usr/src/rr174x-2.4/.build/rr174x.o
  Building modules, stage 2.
  MODPOST 1 modules
[COLOR=Red]WARNING: could not find /usr/src/rr174x-2.4/.build/.him_rr1740pm.o.cmd for /usr/src/rr174x-2.4/.build/him_rr1740pm.o[/COLOR]
  LD [M]  /usr/src/rr174x-2.4/.build/rr174x.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
You made a module which is for current kernel 2.6.35-22-generic.
Deleting previous installed driver module rr174x...
Install the new driver module...
Removing conflicted driver module...
Updating module dependencies...Done.
Checking for initrd images to be updated...
backup /boot/initrd.img-2.6.35-22-generic to /boot/initrd.img-2.6.35-22-generic.rr174x.


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=174494&stc=1&d=1288829934[/IMG]

here it is mounted as NTFS with the original RAID volume from Win2K3
it is working great, speedy and stable, but that compilation error message makes me worry.


So, I'm here trying to figure out "**How to add the EXTRA_CFLAGS or fix the WARNING?**"

and see if i can compile a proper driver module without throwing me a Warning, or having to force the Make to compile / install the module.

I know my way around Linux/BSD/Solaris fairly decently, but i'm no way near good enough to be considerate your average user; I know Windows and Mac inside out which doesn't help me much when i'm on this field.

---

### Post by AllGamer on 2010-11-04
if this is in the wrong forum could a Mod please move it to the proper sub forum?

thank you

---

### Post by AllGamer on 2010-11-08
^ bump ^

10 char

---

### Post by sunnynice on 2010-11-09
> **AllGamer said:**
> if this is in the wrong forum could a Mod please move it to the proper sub forum?
 
thank you
 might be the wrong place.

---

### Post by kekoakeakane on 2010-11-09
Seems this would be the right place to ask this question, but it might get more air time in the "general" area.
 
I'm in the exact same boat as you. I installed a RR1742 on Sunday only to find out that no pre-compiled drivers exists for UBUNTU 10.10. I got the exact error as you did when attemting to build the driver using DKMS. Searched all the libraries that I could think of to no avail. Followed the Highpoint Tech instructions to use "make install" and got the same warning as you. The driver seems to load and if I connect an external drive to it AFTER the server is running, I can access the drive. If I have the drive connected on boot-up, it stalls.
 
I emailed Highpoint Tech support on the error from the DKMS make.log and am awaiting a reply. Will post update on here if/when the reply.

---

### Post by AllGamer on 2010-11-10
Can a moderator please move this topic to the proper area?

Thanks

---

### Post by Iowan on 2010-11-10
> **AllGamer said:**
> Can a moderator please move this topic to the proper area?

ThanksJust this once ;)
Moved to General Help.
The "ReportaAbuse" button might get quicker response...

---

### Post by kekoakeakane on 2010-11-11
Just got a reply back from Highpoint Technologies:
 
"Hello,

We will discuss this with engineering.
The current release has not been tested with this kernel.

Regards,

Customer Support Department"
 
The driver seems to be running fine even with the build warning.  I was able to fix the problem with the system stalling during boot up with the drive connected by flashing the bios.  Will update here when I get a reply from the vendor

---

### Post by AllGamer on 2010-11-19
I'm hesitant to upgrade my full time file server to 10.10 without a perfect driver.

i didn't get that error on previous versions

on my full time server i have another Rocket Raid 1740 + and 2 extra Rocket Raid 2460x1 for a triple layer redundancy

1 Rocket Raid 1740 gets mirrored by another Rocket Raid 1740
same setup for the RAIDs running on the 2460x1

---

### Post by rjksn on 2010-12-26
Thanks @AllGamer!

Just incase anyones as bad at this as me, you're looking for the Open Source driver at the bottom of [http://www.highpoint-tech.com/USA_new/series_rr1700.htm](http://www.highpoint-tech.com/USA_new/series_rr1700.htm)

Download, unarchive in finder/my computer, and then delve into the products folder (there was only one option in each tree for me when I downloaded this which brought me to ~/rr174x-linux-src-v2.4/product/rr1740pm/linux ).

And run
```
sudo KBUILD_NOPEDANTIC=1 make install
```

A quick reboot, and it was showing up correctly. I'm copying over from my non-raid drive to this drive as we speak and it seems to be going well. Hopefully I have no problems getting Netatalk to work with this and my Macs.

---

### Post by AllGamer on 2010-12-28
did you get any warning message during your build compilation?

that's the same command i ran

> **rjksn said:**
> Thanks @AllGamer!

Just incase anyones as bad at this as me, you're looking for the Open Source driver at the bottom of [http://www.highpoint-tech.com/USA_new/series_rr1700.htm](http://www.highpoint-tech.com/USA_new/series_rr1700.htm)

Download, unarchive in finder/my computer, and then delve into the products folder (there was only one option in each tree for me when I downloaded this which brought me to ~/rr174x-linux-src-v2.4/product/rr1740pm/linux ).

And run
```
sudo KBUILD_NOPEDANTIC=1 make install
```

A quick reboot, and it was showing up correctly. I'm copying over from my non-raid drive to this drive as we speak and it seems to be going well. Hopefully I have no problems getting Netatalk to work with this and my Macs.

---

### Post by kekoakeakane on 2010-12-29
> **AllGamer said:**
> did you get any warning message during your build compilation?
 
that's the same command i ran
 
 
I have run this same command at least 4 times with various kernel upgrades with the same warning everytime. So far no issues with the drives. It is quite annoying that the dkms build won't work and I have to manually rebuild the driver and web server each time there is a kernel upgrade. 
 
Of course, I'm not really sure why I keep accepting the kernel upgrades in the first place, but that's a completely separate issue.

---

### Post by AllGamer on 2011-04-25
Yes, in the end i decided to go ahead with it.

It seems to be safe, even if that script was missing.

in the end i found it was way faster to simply run the command

```
sudo make install
```

inside the folder where you find the driver source files.

The rest becomes automatic.

All that is left after that, is to setup the **hptsvr** and **hptraidconf** software to monitor / configure / manage the RAID drives

[http://ubuntuforums.org/showthread.php?t=1737847&highlight=GUI+highpoint](http://ubuntuforums.org/showthread.php?t=1737847&highlight=GUI+highpoint)

---

### Post by babeliak on 2011-05-26
I'm watching this topic, but I prefer to  wait for offcially supported/tested version of RR17xx OpenSource driver for Ubuntu 10.04

So far on 8.04 i get same warning message during compilation:
```
georg@server:~/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux$ sudo make
[sudo] password for georg: 
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-28-generic'
  CC [M]  /home/georg/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/os_linux.o
  CC [M]  /home/georg/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/osm_linux.o
  CC [M]  /home/georg/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/div64.o
  CC [M]  /home/georg/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/hptinfo.o
  CC [M]  /home/georg/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/config.o
  LD [M]  /home/georg/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/rr174x.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/georg/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/.him_rr1740pm.o.cmd for /home/georg/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/him_rr1740pm.o
  CC      /home/georg/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/rr174x.mod.o
  LD [M]  /home/georg/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/rr174x.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-28-generic'
georg@server:~/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux$
```

Using the other parameter gives me the same warning message:
```
georg@server:~/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux$ sudo KBUILD_NOPEDANTIC=1 make
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-28-generic'
  CC [M]  /home/georg/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/os_linux.o
  CC [M]  /home/georg/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/osm_linux.o
  CC [M]  /home/georg/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/div64.o
  CC [M]  /home/georg/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/hptinfo.o
  CC [M]  /home/georg/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/config.o
  LD [M]  /home/georg/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/rr174x.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/georg/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/.him_rr1740pm.o.cmd for /home/georg/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/him_rr1740pm.o
  LD [M]  /home/georg/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/rr174x.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-28-generic'
georg@server:~/Desktop/rr174x-linux-src-v2.4/product/rr1740pm/linux$
```

So far so good, I need to stay with 8.04 LTS

---

