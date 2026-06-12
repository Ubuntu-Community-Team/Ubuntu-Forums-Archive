---
title: "How to stop Ubuntu show up one of my ntfs partition?"
date: 2010-12-30
forum: General Help
---

### Post by jazzi on 2010-12-30
Hi, My hard drive has **2** ntfs partitions, one of them( C: ) is the home of WindowsXP, I don't wanna somebody tap the data,

So can we stop the **C:** partition show up, meanwhile show up another patition**( D: )**?  (D: partition shows up fine now.)

I'm using Ubuntu10.04

thanks.
jazzi

---

### Post by anystupidname1 on 2010-12-30
You need to edit /etc/fstab

Show us
```
fdisk -l
blkid
```please

Alternatively, you could hide the partition in gparted but I think you'd have to unhide it before you boot back to windows every time...

---

### Post by anystupidname1 on 2010-12-30
I'd guess C: is /dev/sda1
```

UUID=blahwhateverC:is /media/winders ntfs-3g noauto 0 0
UUID=blahwhateverD:is /media/automountedDdrive ntfs-3g defaults,force 0 0
```something like that...

Additionally, if you want to prevent ALL automounting:
[http://www.cyberciti.biz/faq/disable-linux-unix-gnome-automounting/](http://www.cyberciti.biz/faq/disable-linux-unix-gnome-automounting/)

---

### Post by jazzi on 2010-12-30
Thanks, I'll post the /etc/fstab tonight I'm in office now.

I know in Ubuntu10.04 when we click the ntfs icon it will mount the partition, now how to let the ntfs partition icon disapper?

thanks

---

### Post by anystupidname1 on 2010-12-30
See previous response :biggrin:

---

### Post by jazzi on 2010-12-30
**gconf-editor**, someone said it can make the ntfs icon disappear.

---

### Post by jazzi on 2010-12-31
Sorry the right question subject should be: how to hide partition from place menu?

and finally I found the answer from [http://newyork.ubuntuforums.org/showthread.php?t=1642958&page=6](http://newyork.ubuntuforums.org/showthread.php?t=1642958&page=6)

1, show up the details of your partitions
```
sudo blkid
```

> /dev/sda1: LABEL="System_restore_win7" UUID="DAA41C49A41C2B11" TYPE="ntfs" 
/dev/sda2: LABEL="Windows_7_boot" UUID="921C18621C18441F" TYPE="ntfs" 
/dev/sda3: LABEL="Windows_7" UUID="A2984D43984D1767" TYPE="ntfs" 
/dev/sda5: LABEL="Ubuntu_10.04" UUID="3d48429c-7361-4ab8-8689-54407673b141" TYPE="ext4" 
/dev/sda6: UUID="b1c6171a-075e-4291-af69-64baf751d10e" TYPE="swap" 
/dev/sda7: LABEL="OpenSuse" UUID="56a4c951-b189-45cb-91e6-76c83b765044" TYPE="ext4" 
/dev/sda8: LABEL="natty" UUID="fb661c9e-e56a-413b-bef4-dc2e0db8c0b1" TYPE="ext4" 
/dev/sda9: LABEL="Fedora-14" UUID="3d35b416-3b1b-467d-892c-ac2095c0ab18" TYPE="ext4" 
/dev/sda10: LABEL="Arch_Linux" UUID="6aa72302-2b4f-432c-953a-33c7513bfa47" TYPE="ext4" 

2, create a new file
```
sudo vim /etc/udev/rules.d/hide--partitions.rules
```
> 
ACTION!="add|change", GOTO="hide_partition_end"
SUBSYSTEM!="block", GOTO="hide_partition_end"
KERNEL=="loop*|ram*", GOTO="hide_partition_end"

KERNEL=="sda2", ENV{UDISKS_PRESENTATION_HIDE}="1"

LABEL="hide_partition_end"

sda2 is my windows boot partition, I don't wanna let anyone see it.

---

