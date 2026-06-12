---
title: "how to disable ntfs support in ubuntu"
date: 2012-08-17
forum: General Help
---

### Post by jebi on 2012-08-17
hi
 
re how to disable ntfs support in ubuntu
 
i am a complete noob to ubuntu so please give idiots guide to me
 
i have my pc dual booting windows and lastest ubuntu, but i want to keep the 2 os's completely apart windows does not see the ubuntu partitions, but ubuntu sees the windows partitions. ubuntu gives me the option to mount the windows partition.
 
is there a way before or during ubuntu installion to unintsall ntfs support? or to do it after installion?.
 
many thx
 
please remember complete noob step by step idiots instructions..

---

### Post by raja.genupula on 2012-08-17
yeah there is way . remove ntfs-3g package . 

to do so```
 sudo apt-get remove ntfs-3g
```

then give a restart to apply the changes . 

in future if you want to revert to back then 

```
sudo apt-get install ntfs-3g 
```

that will get it back .

---

### Post by oldfred on 2012-08-17
You can also just hide the mount in / (root) or just set to read only so you can read info if you want but not write or do any harm to Windows.

Hide mount 
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
Hide windows mount with noauto: 777 is no permissions at all
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0

Set windows boot partition Read only - Morbius1:
After Ubuntu has done it's thing I usually go in and change the umask to 227 which will make the C Drive read only.
/dev/sda1 /media/sda1 ntfs nls=iso8859-1,ro,umask=227 0 0 

Mount in /media or /home will show in Nautilus left panel mounts in / or /mnt will not.

---

### Post by sakamoto on 2012-08-20
agreed -removing ntfs-3g is not the best way

---

### Post by Morbius1 on 2012-08-20
> **sakamoto said:**
> agreed -removing ntfs-3g is not the best way
Especially since one day in the future the user will purchase a multi-terabyte external hard drive formatted in ntfs and have to install ntfs-3g again to use it.

oldfred has the answer:

Cretate mount points for all the ntfs formatted partition that you don't ever want to access, for example:
```
sudo mkdir /WinC
```Then find the correct uuid number for your partition with this command:
```
sudo blkid -c /dev/null
```And add a line to /etc/fstab to prevent it from being used:
```
UUID=xxxxxxxxxxxxxxx /WinC ntfs defaults,noauto,ro,umask=227 0 0
```There's so many levels of redundancy in that line it's embarrassing ;)

**noauto** = will prevent the partition from being mounted automatically at boot.
[COLOR=Blue][I]It can still be mounted but only by root or sudo but only from the terminal and only to /WinC.

[/I][COLOR=Black]**ro** = will mount it read only if you were to mount it as root.
**umask=227** is a belt and suspenders kind of thing that will make sure that if it ever is mounted by root or sudo that it mounts as read only to root and inaccessible to everyone else.
[/COLOR][/COLOR]

---

