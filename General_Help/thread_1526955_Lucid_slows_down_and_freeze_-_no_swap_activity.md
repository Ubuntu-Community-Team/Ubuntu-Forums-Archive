---
title: "Lucid slows down and freeze - no swap activity"
date: 2010-07-08
forum: General Help
---

### Post by jfl on 2010-07-08
Upgraded to 10.04 two months ago (32 bit)
Everything working fine.
The only application running all the time is OpenOffice spreadsheet.
Occasionally Firefox.
All updates are done.
Yesterday, boot was slower than usual, then, after 10 minutes working on the spreadsheet, the machine froze solid, had to hard reboot.
Same thing.
Rebooted again, still slower, got the "System monitor" running, and noticed that the memory use was increasing and got to the limit (512) but **there was no swap activity ???** 
The swap partition is big, (1 gb). There is a lot of space on this HD ...
Hard drive checks "healthy"
Running dual boot on 2 HDs with W2K.
Trying to avoid re-installing, I don't have much time.

It is an office machine, so I am catching some flak about Ubuntu :(

Any suggestions ?          THANKS !

---

### Post by NCLI on 2010-07-08
Could you post the output of "cat /proc/sys/vm/swappiness"

---

### Post by jfl on 2010-07-08
Thanks for the reply; office is closed, I'll do it tomorrow !

---

### Post by jfl on 2010-07-09
OK, the result of ""cat /proc/sys/vm/swappiness" " is **60.**

Also here is fstab, just in case:

```
jf@monique:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=1cdc3133-5892-4966-a152-a7899e19a5ff /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=56145584-a886-415d-93a8-8bf6cdc8ac5d /boot           ext3    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=526c71f8-b5f8-499f-83c0-ea9da01f19a1 /home           ext3    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=9085f16a-ba97-4a48-9cb8-95fcc72c55d3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Also, when I start the "System monitor", the CPU goes to 100% even though there is a total of 50 -70 % in the process list ???

Thanks for any suggestions !

---

### Post by plucky on 2010-07-09
Please post output of ```
free -m
sudo blkid
```

---

### Post by jfl on 2010-07-09
Forgot to mention that in the boot, during the Splash screen, when the little red and white dots appear, there is a line of text below but it disappear so quickly I cannot read it.

Thanks for any pointers !

---

### Post by jfl on 2010-07-09
> **plucky said:**
> Please post output of ```
free -m
sudo blkid
```

Here it is:

```
jf@monique:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           465        403         62          0         70        174
-/+ buffers/cache:        158        307
Swap:            0          0          0
jf@monique:~$ sudo blkid
/dev/sda1: UUID="56145584-a886-415d-93a8-8bf6cdc8ac5d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="05cc57e2-3c56-4819-bb53-bfde34aed764" TYPE="swap" 
/dev/sda3: UUID="1cdc3133-5892-4966-a152-a7899e19a5ff" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="526c71f8-b5f8-499f-83c0-ea9da01f19a1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: UUID="625C2B895C2B56D7" TYPE="ntfs" 
/dev/sdb5: LABEL="Apps" UUID="0F55E8CFB7705589" TYPE="ntfs" 
/dev/sdb6: LABEL="Data" UUID="AE8C31DC8C319FAF" TYPE="ntfs" 
/dev/sdb7: LABEL="FAT32" UUID="4564-22DB" TYPE="vfat"
```

---

### Post by jfl on 2010-07-09
Found the "swap" problem.
Went in "gparted" and noticed the swap partition was inactive; I did "swapon" and it works !
Now, how did the the swap got turned off, I'll probably never know ;)

Now, we'll see if the performance is back like it was a few days ago.

Thanks guys, for your help !

---

### Post by plucky on 2010-07-10
From fstab ```
# swap was on /dev/sda2 during installation
UUID=9085f16a-ba97-4a48-9cb8-95fcc72c55d3 none            swap    sw              0       0

```
From sudo blkid ```
/dev/sda2: UUID="05cc57e2-3c56-4819-bb53-bfde34aed764" TYPE="swap" 

```

That means that the next time you reboot,your swap partition will not mount and swap will be off.
You should edit your fstab file and change the uuid for your swap partition to the one given by the sudo blkid command.

> Swap:            0          0          0

From the free -m command that shows that swap is off.


Good Luck

---

### Post by jfl on 2010-07-11
You are right Plucky; on reboot the swap is off again.
I changed the UUID as suggested, now swap is on when I reboot.

Thanks !!!

Now we'll see Monday if the speed is back !

---

### Post by jfl on 2010-07-14
Working fine now !
Thanks.

---

