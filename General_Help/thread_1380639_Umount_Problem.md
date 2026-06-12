---
title: "Umount Problem"
date: 2010-01-13
forum: General Help
---

### Post by JvIasterMind on 2010-01-13
Hello,

I am writing a program in c++ and qt that requires mounting and unmounting compact flash cards. I am accomplishing this though the system() commands using *mount* and *umount*.

The problem I am having is that when unmounting the drives, every drive gets unmounted and leaves the mountpoint directory behind, except one device (sdc) has the mountpoint directory deleted automatically during the process.


So for example...

I plug in three compact flash cards that are identical and formatted in fat32. Here is the output of fdisk -l...
```

Disk /dev/sdc: 2029 MB, 2029805568 bytes
255 heads, 63 sectors/track, 246 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00022752

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         246     1975963+   b  W95 FAT32

Disk /dev/sdk: 2029 MB, 2029805568 bytes
255 heads, 63 sectors/track, 246 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x001c2022

   Device Boot      Start         End      Blocks   Id  System
/dev/sdk1               1         246     1975963+   b  W95 FAT32

Disk /dev/sdg: 2029 MB, 2029805568 bytes
255 heads, 63 sectors/track, 246 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x001c2022

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1         246     1975963+   b  W95 FAT32

```Now, since the cards were automatically mounted by the system, I unmount all three cards using the following commands...
```

root@ubuntu-flash:~# umount /dev/sdc1
root@ubuntu-flash:~# umount /dev/sdk1
root@ubuntu-flash:~# umount /dev/sdg1

```Then I make the directories and mount the cards to these new directories...
```

root@ubuntu-flash:~# mkdir /mnt/sdc
root@ubuntu-flash:~# mkdir /mnt/sdk
root@ubuntu-flash:~# mkdir /mnt/sdg
root@ubuntu-flash:~# mount /dev/sdc1 /mnt/sdc
root@ubuntu-flash:~# mount /dev/sdk1 /mnt/sdk
root@ubuntu-flash:~# mount /dev/sdg1 /mnt/sdg

```Everything is good at this point and all the commands did what I have been expecting. But now, I want to unmount the cards with the following commands...
```

root@ubuntu-flash:~# umount /dev/sdc1
root@ubuntu-flash:~# umount /dev/sdk1
root@ubuntu-flash:~# umount /dev/sdg1
 
```They all were unmounted, but for some reason /mnt/ only has the sdg and sdk folders... the sdc folder gets deleted when I used the umount command.
```

root@ubuntu-flash:~# ls /mnt/
sdg  sdk

```I can even change the order of the cards. The system always deletes whatever folder /dev/sdc1 gets mounted into.


Since my program is automating this process, I am hoping someone can help me get around this issue by hopefully figuring out why the one device behaves differently from the others.

Thank you in advance,
JvIasterMind

---

