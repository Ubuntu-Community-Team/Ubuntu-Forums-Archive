---
title: "Old OS not in GRUB"
date: 2006-02-10
forum: General Help
---

### Post by dotancohen on 2006-02-10
I have two hard drives- hda and hdb. Windows XP Home is installed in hdb6 and until yesterday was the only OS on this machine (I know that is unusual. That is the situation after an earlier attempt at Fedora). When I installed Kubuntu to hda today I changed the BIOS setting so that the machine will boot from hda. But Windows is not in the GRUB menu. What must I do to make it be there? Even when I configure BIOS to boot from hdb it won't load windows now.

Thanks in advance.

Dotan Cohen
[http://technology-sleuth.com/technical_answer/what_is_a_router.html](http://technology-sleuth.com/technical_answer/what_is_a_router.html)

---

### Post by codejunkie on 2006-02-10
[QUOTE=dotancohen]I have two hard drives- hda and hdb. Windows XP Home is installed in hdb6 and until yesterday was the only OS on this machine (I know that is unusual. That is the situation after an earlier attempt at Fedora). When I installed Kubuntu to hda today I changed the BIOS setting so that the machine will boot from hda. But Windows is not in the GRUB menu. What must I do to make it be there? Even when I configure BIOS to boot from hdb it won't load windows now.

Thanks in advance.

Dotan Cohen
[http://technology-sleuth.com/technical_answer/what_is_a_router.html](http://technology-sleuth.com/technical_answer/what_is_a_router.html)[/QUOTE]
try ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```
then ```
sudo gedit /boot/grub/menu.lst
```
and copy and paste this in your menu.lst file
```

title		Microsoft Windows
root		[COLOR="Blue"](hd0,0)[/COLOR]
savedefault
makeactive
chainloader	+1

```
you have to adjust [COLOR="Blue"](hd0,0)[/COLOR] to your drive and partition guessing from how you described your setup im thinking it should be (hd1,6) but if you have swap partitions on there i dont think it counts them, so you might have to tinker a bit with that last drive number according to how that drive is partitioned.

---

### Post by nkhansen on 2006-02-10
How does your /boot/grub/menu.lst look?

You should have something like this at the bottom:

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader +1

You should probably change (hd0,0) to (hd1,5) or something like that.

---

### Post by dotancohen on 2006-02-10
Thanks. I didn't have an entry for windows in there at all. I just added what seemed neccassary, and I will play with the (0,0) (1,6) options till I get it right.

What is the meaning of chainloader +1, makeactive, and savedefault? The other options in GRUB did not have these. (Kubuntu, memtest)

---

### Post by dotancohen on 2006-02-10
None of the (1,0)  (1,6) works...

Two questions:
1) Could I / should I remove the chainloader attribute?
2) How can I edit /boot/grub/menu.1st from the GRUB command prompt? Is there not an editor? Must I boot the system to edit the file?

Thanks in advance.

---

### Post by Lord Illidan on 2006-02-10
What is your partitioning scheme?

Give us an overview of your partitions and harddisks and your /etc/fstab so we can  see if we can find a solution.

Do not remove the chainloader attribute. I don't know exactly what it does, but it is important, so don't mess with it.

---

### Post by RaisedFist on 2006-02-10
Better than this. Run **cfdisk** and see what's your Windows partition. It shows you exactly what you need.

---

### Post by dotancohen on 2006-02-10
Here is fstab:
```

dotancohen@ety:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hda2 / ext3 defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hda8 /home ext3 defaults,atime,auto,rw,dev,exec,suid,nouser 0 2
/dev/hda7 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0 /media/floppy0 auto ,atime,noauto,rw,dev,exec,suid,user 0 0
/dev/hdb5 /mnt/music vfat noauto,uid=1000,gid=1000,auto,rw,users 0 0
/dev/hdb6 /mnt/windows vfat noauto,uid=1000,gid=1000,auto,rw,users 0 0
/dev/hda5 /mnt/pictures vfat noauto,uid=1000,gid=1000,auto,rw,users 0 0
/dev/hda6 /mnt/win_home vfat noauto,uid=1000,gid=1000,auto,rw,users 0 0

```

As you can see the windows partition is hdb6. hda6 is something else (D drive for my personal home folder).

Yes, they are FAT32 partitions I did that on purpose.

---

### Post by dotancohen on 2006-02-10
[QUOTE=RaisedFist]Better than this. Run **cfdisk** and see what's your Windows partition. It shows you exactly what you need.[/QUOTE]

I got:
```
FATAL ERROR: Cannot open disk drive
Press any key to exit cfdisk
```

---

