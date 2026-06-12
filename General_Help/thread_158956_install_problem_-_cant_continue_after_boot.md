---
title: "install problem - cant continue after boot"
date: 2006-04-12
forum: General Help
---

### Post by asafdav2 on 2006-04-12
i finished the first installation phase (defining and formating a partition, installing grub etc') and reboot the computer. the problem - when booting, i have no way to continue with the installation. instead i get the usual OS choosing screen, where i have 2 instances of windows xp (the second one is of an old windows install i once had and i dont know how to remove it. i just hit enter to select the first). if i choose the first i boot normally into windows. i tried the ubuntu installation twise and got the same result both times. any idea what to do?

thanks a bunch:)

---

### Post by justleen on 2006-04-12
Are you sure grub is being installed? The OS selection screen, is that windows' , or grubs?

---

### Post by Herman on 2006-04-12
You should be able to help GRUB find the linux kernel (vmlinuz) and boot Ubuntu from Grub's command line, [see this link]("http://www.users.bigpond.net.au/hermanzone/p15.htm") for more details. 
If you try hard and still can't do it and you find GRUB too hard for you, try [GAG]("http://www.users.bigpond.net.au/hermanzone/p12.htm") instead.
(Herman)

---

### Post by slug on 2006-04-12
Try going into the grub console and playing with the following commands to see what works. 
To get into the GRUB console type c at the boot menu.
(If you get error messages with any of these commands TAB completion is a great help to "discover" what's availible)


```
root (hd0,0)
```
This will set the root drive and partition for grub to look for the kernel.
hd0 normally indicates /dev/hda and hd1 normally indicates /dev/hdb.
You can type root (hd[COLOR="Red"]TAB[/COLOR],[COLOR="Red"]TAB[/COLOR]) Where [COLOR="Red"]TAB[/COLOR] is the TAB key on your keyboard to list the drive and partitions availible


```
kernel /boot/vmlinuz-[COLOR="Green"]VERSION[/COLOR] root=/dev/[COLOR="Blue"]hda1[/COLOR] ro quiet splash
```
This command tells GRUB which linux kernel version to load.
Replace [COLOR="Green"]VERSION[/COLOR] with your kernel version number (TAB completion also works here)
Replace /dev/[COLOR="Blue"]hda1[/COLOR] with the partition that ubuntu's installed to.

```
initrd /boot/initrd.img-[COLOR="Green"]VERSION[/COLOR]
```
This specifies the initial ramdisk for a Linux format boot image and set the appropriate parameters in the Linux setup area in memory.
Replace [COLOR="Green"]VERSION[/COLOR] with your kernel version number (TAB completion also works here)

```
savedefault
```
Not too sure what this does :S

```
boot[/CODE
Tells grub to launch the boot process



Here is an example of what's required to start ubuntu
[CODE]
root (hd0,0)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hdc1 ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot

```



Hope this helps, 
If this still doesn't work, try posting your drive and partition configuration.

---

### Post by asafdav2 on 2006-04-12
ok, update.

here's my drives / parts setup
[U]
80GB HD: [/U]
1 partition of 80GB, serves as storage (used to have windows installed on it)

_250GB HD: _
1 Partition of ~15GB, serves as windows XP specific partition            
2 Partitions of 80GB each, serves as storage
1 (new) partition of 15G, where i installed Ubuntu

i feared the ubuntu setup recognized the master boot drive as the wrong one, i.e C:, the drive that had the old win install

so i reinstalled and this time when asked about installing grub, i said no and when asked to specifiy a location for it, i said (hd1) (i guess insted of hd0)

the good news is that now i do get Grub screen on boot.
the bad news are that things dont work so well now. I'll try to give as much details as i can.

in the grub screen, I have 5 options - 

```
Ubuntu, Kernell 2.16.12-9-386
Ubuntu, Kernell 2.16.12-9-386 (recovery mode)
Ubuntu, Memtest86+
Other operating system
Windows NT/2000/XP (loader)
```

when choosing any of the first 3, i get :

```
Booting 'Ubuntu, Kernell 2.16.12-9-386'
root (hd0,6)
Error 22: No such partition
Press any key to continue...
```

when choosing 'other OS', nothing happens

when choosing 'Windows NT/2000/XP (loader), i get :

```
root (hd1,0)
File system type unknown, partition type 0x7
save default
map (hd0)(hd1)
map (hd1)(hd0)
chainloader +1

NTLDR is missing
Press ctrl+alt+del to restrart
```

when pressing 'e' on Ubuntu, Kernell 2.16.12-9-386, i get

```
root (hd0,6)
kernel /boot/vmlinuz-2.6.12-9-386 root= /dev/sdat ro quiet splash
initrd /bootinitrd.img-2.6.12-9-386
savedefault
boot
```

when pressing 'e' on windows, i get

```
root (hd1,0)
savedefault
map (hd0)(hd1)
map (hd1)(hd0)

chainloader +1
```

this is basiaclly it, if you need any more details just ask

thanks again

---

### Post by slug on 2006-04-12
> i feared the ubuntu setup recognized the master boot drive as the wrong one, i.e C:, the drive that had the old win install
This sometimes happens, in fact on my computer ubuntu recognises my drive order correctly. 
[I]Onboard Primary master /dev/hda (hd0)
Onboard Secondary master /dev/hdb   (hd1)
PCI Controller Raid Drive /dev/hde (hd2)[/I]

When I boot, grub sees the following
[I]Onboard Primary master /dev/hda (hd0)
Onboard Secondary master /dev/hdb (hd2)
PCI Controller Raid Drive /dev/hde (hd1)[/I]

**# cat /boot/grub/device.map** returns 
> 
(hd0)   /dev/hda
(hd1)   /dev/hdc
(hd2)   /dev/hde
(hd3)   /dev/hdg



The way i figured out how grub maps it's drives is by playing with the grub console at boot.
After successfully booting into ubunto, edited the menu.lst file accordingly and voilla!

Try it, and remember, tab completion is your friend...

---

### Post by slug on 2006-04-12
> Booting 'Ubuntu, Kernell 2.16.12-9-386'
root (hd0,6)
Error 22: No such partition
Press any key to continue... 

here's your problem.
At the grub console type root (hd0,[COLOR=Red]TAB[/COLOR]) to see what partitions are availible

use trial and error to figure out which one you should use...

---

### Post by asafdav2 on 2006-04-12
small update - 
(hd0) had no usable partitions (when pressing tab all i got was hd0,0), however turns out the correct partition was (hd1, 6). so i edited the commands and it booted ok into ubuntu and installing at the moment.
however, i'm still in fear about the XP boot - i guess i'll have to wait for it to finish installing to make sure it still doesnt work, but if anyone has any idea about things i need to change, i'd love to hear

thanks

---

### Post by slug on 2006-04-12
If it doesn't work now, it probably won't work after..

When the post installation process is finished, login and post the results of
**sudo fdisk -l**

---

### Post by asafdav2 on 2006-04-12
```
Device boot     ID      System
/dev/sda1        7     HPFS/NTFS
/dev/sda2        f    W95 Ext'd (LBA)
/dev/sda5        7     HPFS/NTFS
/dev/sda6        7     HPFS/NTFS
/dev/sda7        83      LINUX

```


update : ok, i got it to work
the map commands were redundent, seeing the windows install was on the same drive as the linux

---

