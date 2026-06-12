---
title: "windows xp won't boot after installing natty narwhal"
date: 2011-04-11
forum: General Help
---

### Post by yama.one on 2011-04-11
in the grub menu once I select windows and press enter the screen goes dark and then it takes me back to the grub menu again.

both ubuntu 11.04 and win xp are installed on the same harddisk


```

setparams 'windows (on /dev/sda1)'

insmod part_msdos
insmod ntfs
set root = '(/dev/sda_msdos1)'
search --no-floppy --fsuuid --set=root XXXXXXXXXXXX
drivemap -s (hd0) ${root}
chainloader +1


```

---

### Post by 3Miro on 2011-04-11
Go into Ubuntu, start the terminal (search for terminal in the Natty menu), then type the following:

```
sudo fdisk -l
```

It will ask you for password and then it will display the layout of your HDD. Post the layout here so we can see where windows is and what is going on.

---

### Post by yama.one on 2011-04-11
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x307803db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4857    39013821    7  HPFS/NTFS
/dev/sda2            4858        9730    39136773    f  W95 Ext'd (LBA)
/dev/sda5            4858        5175     2549448   83  Linux
/dev/sda6            9538        9730     1539072   82  Linux swap / Solaris
/dev/sda7            5175        7220    16429160   83  Linux
/dev/sda8            9352        9538     1486848   82  Linux swap / Solaris
/dev/sda9            7220        9256    16354304   83  Linux
/dev/sda10           9257        9351      761856   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by 3Miro on 2011-04-11
Back in the terminal, type:
```
gksudo gedit /etc/grub.d/40_custom
```

a windows will popup and you will have to add the following at the END of the file:

```

menuentry "Windows"{
set root=(hd0,1)
chainloader +1
}

```

Save and exit. Afterwards, run:
```
sudo update-grub
```

Reboot. If it doesn't work, you can try:
```

menuentry "Windows"{
set root=(hd0,2)
chainloader +1
}

```
(with sudo update-grub again)

---

### Post by yama.one on 2011-04-11
doesn't work :(

---

### Post by 3Miro on 2011-04-11
Did you try both of those? What exactly is the error?

How about:
```

menuentry "Windows"{
set root=(hd0,1)
chainloader (hd0,1)+1
}

```

If this doesn't work, can you enter the windows partition (Home -> Places and the partitions will be to the left). Then look for "boot.ini" file and post the content here.

---

### Post by yama.one on 2011-04-11
yeah both of them didn't work, the first one dark screen and it returns me to the grub menu again, the second one says the partition is not found or something like that.

```
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```it is partition 1, but I don't know why it is refusing to boot.

---

### Post by 3Miro on 2011-04-11
At this point I don't know, everything looks setup correctly. We may have to wait for someone more knowledgeable with more experience in windows booting.

---

### Post by yama.one on 2011-04-11
thanks anyway

i will try to fix the MBR and start a fresh installation.

---

### Post by Wanas on 2011-04-29
Im having the same problem I will reinstall ubuntu to see if this will help

---

