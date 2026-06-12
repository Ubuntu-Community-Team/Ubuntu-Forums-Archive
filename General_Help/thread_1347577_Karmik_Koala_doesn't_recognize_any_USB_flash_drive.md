---
title: "Karmik Koala doesn't recognize any USB flash drive."
date: 2009-12-06
forum: General Help
---

### Post by crist360 on 2009-12-06
I'm getting bored of Ubuntu, since I started using this OS, I have had lots of problems, I use to receive many error messages, I have reinstalled the system several times because it starts to fail, it becomes slow, etc. 

My last problem is the following: I have been using Karmik Koala for some weeks on my desktop pc, but the problem is that it doesn't recognize any USB flash drive, when I use the command **lsusb** I receive this message: 

Bus 001 Device 008: ID 0951:1613 Kingston Technology 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1019:0c55 Elitegroup Computer Systems (ECS) Flash Reader, Desknote UCR-61S2B
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 002 Device 002: ID 045e:00dd Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I cannot use any pendrive on my system, I have been researching on many websites, but there isn't any solution. These kinds of problems are the ones that make me think on coming back to the OS with the little windows.
 
Please, I need some help.

---

### Post by paradigm2 on 2009-12-06
I have a little usb flash drive I just bought but have yet to try it on Karmic.  However from what you said about slow downs and wierd problems I wouldn't rule out hardware issues.  Ubuntu has been very solid for me....

---

### Post by Vishnu V on 2009-12-06
Can you post the output of
```

sudo fdisk -l

```

---

### Post by crist360 on 2009-12-06
> **Vishnu V said:**
> Can you post the output of
```

sudo fdisk -l

```

This is the message I receive by typing **sudo fdisk -l**: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe1e4e1e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19083   153284166   83  Linux
/dev/sda2           19084       19457     3004155    5  Extended
/dev/sda5           19084       19457     3004123+  82  Linux swap / Solaris

Disk /dev/sdf: 4011 MB, 4011851776 bytes
124 heads, 62 sectors/track, 1019 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Disk identifier: 0x00027619

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        1019     3917005    b  W95 FAT32


Right now I'm adding these lines :

# Mount usb
UUID= 0x00027619
#/dev/sdf1     /media/usb vfat users,exec,noauto,noatime,rw 0 0

 to the file **fstab. **I'm following some instructions from another website, but I don't know whether it is going to work or not. This problem started to happen when I updated my system to Karmik koala, on Jaunty everything worked out of the box.

---

### Post by Vishnu V on 2009-12-06
please comment the line UUID= 0x00027619 on fstab file by adding # in the front of the line

if that fails try to mount the usb manually as follows
```

sudo mkdir /media/usb         
sudo mount -t vfat /dev/sdf1 /media/usb

```

---

### Post by crist360 on 2009-12-06
> **Vishnu V said:**
> please comment the line UUID= 0x00027619 on fstab file by adding # in the front of the line

if that fails try to mount the usb manually as follows
```

sudo mkdir /media/usb         
sudo mount -t vfat /dev/sdf1 /media/usb

```

I followed every step but nothing happened, indeed, I couldn't mount my usb flash drive manually. Karmic doesn't recognize any usb drive, there are lots of people with the same problem in other forums, but no one has found a solution. [-(

I'll try to find more information about it. If I can't solve this problem, I'll come back to Jaunty...

thanks!

---

### Post by Vishnu V on 2009-12-06
> **crist360 said:**
> I followed every step but nothing happened, indeed, I couldn't mount my usb flash drive manually. Karmic doesn't recognize any usb drive, there are lots of people with the same problem in other forums, but no one has found a solution. [-(

I'll try to find more information about it. If I can't solve this problem, I'll come back to Jaunty...

thanks!

Is there any error when you tried to mount usb manually ?

---

### Post by crist360 on 2009-12-08
> **Vishnu V said:**
> Is there any error when you tried to mount usb manually ?

At the beginning, when I tried to mount my usb manually, nothing happened... But yesterday it worked fine, it is the only way to see the content of my pendrive, the thing is that I want my system to recognize every usb flash drive automatically, I don't want to use the terminal for something so basic like using a pendrive.

---

### Post by Vishnu V on 2009-12-09
Can u check this ?. Type this in terminal
```

gconf-editor /apps/nautilus/preferences/media_automount

```
and check this option if it is not checked

---

### Post by SteveNorman on 2009-12-09
I would plug it in and check ```
dmesg | tail
```

look for /dev/sdd or something to that effect, and add an fstab or just mount it to a mount point manually using the name in dmesg.

Are your pendrives formated to fat32 for a reason? if your not using them on windows you can take them and put ext3 or 4 on them before using them.


also, no need to update your OS every 6 months, The last Ubuntu I really liked was 8.04. Why upgrade if your stuff is working? If you still have the option in grub just set 9.04 as your default os to boot to till you get 9.10 ironed out since things worked there. You may have overwritten a config file somewhere. Also you may want to think about debian due to its stability, but you will do more work to get it where you want it.

---

### Post by crist360 on 2009-12-10
> **Vishnu V said:**
> Can u check this ?. Type this in terminal
```

gconf-editor /apps/nautilus/preferences/media_automount

```and check this option if it is not checked

The automount option is checked, I analysed all those options and everything seems to be fine, but usb flash drives are still unrecognizable.

---

### Post by prem1er on 2009-12-10
Is the port working? If you plug a usb mouse or keyboard into the same usb port does it work?

---

### Post by crist360 on 2009-12-10
> **SteveNorman said:**
> I would plug it in and check ```
dmesg | tail
```look for /dev/sdd or something to that effect, and add an fstab or just mount it to a mount point manually using the name in dmesg.

Are your pendrives formated to fat32 for a reason? if your not using them on windows you can take them and put ext3 or 4 on them before using them.


also, no need to update your OS every 6 months, The last Ubuntu I really liked was 8.04. Why upgrade if your stuff is working? If you still have the option in grub just set 9.04 as your default os to boot to till you get 9.10 ironed out since things worked there. You may have overwritten a config file somewhere. Also you may want to think about debian due to its stability, but you will do more work to get it where you want it.

Thanks, but it didn't work. I don't know why I have had so many problems with Karmik, I've read on many websites that this distro is the Canonical's Vista, perhaps it's true! What you say is absolutely true, it isn't necessary to update our systems every six months. Jaunty worked awesome on my systems, but as I read lots of times about the faster and great new Karmik, I decided to try it, what a mistake! I also have an Acer Aspire One (flash memory version) running Jaunty, but when I start my system I receive an error which says: grub stage 1.5 loading please wait... error 2.

Hahaha, I'm really fed up of all these problems... I have been researching on many forums and there are lots of different "solutions", but nothing works and just a few people have solved that problem ahahaha. Anyway, I'll decide what to do with Ubuntu and I'll try Debian too, the last alternative is to come back to the OS with the little windows. 

Thanks fellas.

---

### Post by crist360 on 2009-12-10
> **prem1er said:**
> Is the port working? If you plug a usb mouse or keyboard into the same usb port does it work?

Yup, it is working. I have been using my printer in the same ports and also connected my mouse and everything works fine, except for pendrives.

---

### Post by Vishnu V on 2009-12-11
try 
add
```

/dev/sdf1	/media/usb		vfat		user,auto,fmask=0111,dmask=0000

``` this to the end of
to /etc/fstab

Here also  there will be problem you can use only one usb flash drive at a time

---

### Post by crist360 on 2009-12-11
> **Vishnu V said:**
> try 
add
```

/dev/sdf1    /media/usb        vfat        user,auto,fmask=0111,dmask=0000

``` this to the end of
to /etc/fstab

Here also  there will be problem you can use only one usb flash drive at a time

Hey, I'll have to take a star from the sky and give it to you hahahaa. Your solution is the only one that really works. Thanks a lot! :D At last I can use pendrives without so many problems, I still wonder why Karmik has given so many problems recognizing USB flash drives (there are lots of posts about it in different forums). Thanks Vishnu!

---

