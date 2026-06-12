---
title: "mounted dd image seems to be scrambled"
date: 2010-04-27
forum: General Help
---

### Post by czerwinski1977 on 2010-04-27
Hi there,

I am desperately trying to make an image of a partition from my old notebook (openSUSE/ext3) via LAN.

Since I am short on external media, I do a dump of the partition via network from the source PC:

[FONT="Courier New"]dd if=/dev/sda1 bs=512 count=55777680 |ssh rm@192.168.1.1 "cat >/home/rm/temp/sda1_file"[/FONT]

This actually works nicely, the image is on the target PC (192.168.1.1) in place. I can even mount it:

[FONT="Courier New"]mount -o loop,ro sda1_file sda1_mnt[/FONT]

But the directory looks really bad:
[FONT="Courier New"]~/temp/sda1_mnt$ ll
ls: cannot access mnt: Input/output error
ls: cannot access root: Input/output error
ls: cannot access srv: Input/output error
ls: cannot access .Xauthority: Input/output error
total 658250639
drwxr-xr-x    25 root       root             4096 2010-04-27 20:52 ./
drwxr-xr-x     6 rm         rm               4096 2010-04-28 00:17 ../
-rw-r--r--     1 root       root              289 2009-08-21 13:14 .bash_history
-rw-r--r--     1 root       root             5516 2009-10-27 09:43 bin
-rwxr-xr-x     1 root       root           116756 2009-10-24 06:47 boot*
-rw-r--r--     1 rm         users           28455 2009-12-23 11:29 core
-rw-r--r--     1 root       root             3431 2009-09-10 00:13 dev
-rw-r--r--     1 root       root             1655 2009-10-24 07:51 etc
lrwxrwxrwx     1 root       root               10 2008-06-29 13:14 etc.bak -> ../boot.md
srwxr-xr-x     1 rm         users               0 2009-02-05 08:24 home=
-rw-r--r--     1 root       root             1582 2009-11-15 04:09 index.html
-rw-r--r--     1 root       root             2409 2005-09-10 10:27 lib
drwx------     2 root       root            16384 2009-11-14 18:32 lost+found/
-rw-r--r--     1 root       root              814 2009-11-15 12:36 lsmod.11.2
-r--r--r--     1 root       root            49511 2008-07-25 19:20 .mc
-rw-r--r--     1 root       root             2459 2009-10-20 14:55 media
d?????????     ? ?          ?                   ?                ? mnt/
-rwxr-xr-x     1 root       root             9804 2009-10-24 05:46 opt*
-rw-r--r--     1 root       root           250377 2009-11-15 02:32 pkglist.txt
?--sr--r-x 13690 1146184549 1397714549 1650553973 2031-05-07 07:00 proc
d?????????     ? ?          ?                   ?                ? root/
-rw-r--r--     1 rm         users             895 2009-01-09 16:40 sbin
-rw-r--r--     1 root       root             1310 2007-11-26 20:01 selinux
d?????????     ? ?          ?                   ?                ? srv/
-rw-r--r--     1 rm         users           12402 2010-04-27 20:08 success
drwxrwxrwx     2 www-data   www-data         4096 2010-01-29 19:07 sys/
drwx------     2 rm         users            4096 2010-01-17 23:53 tmp/
-rw-------     1 rm         users           34187 2009-12-28 12:22 transactions.db
drwxr-xr-x     4 root       root             4096 2009-10-24 02:47 usr/
drwxr-xr-x    15 root       root             4096 2010-02-14 01:30 var/
-rw-r--r--     1 root       root             2797 2009-11-05 14:53 .viminfo
-rw-r--r--     1 root       root                0 2010-03-17 16:26 .vmware
-rwxr-xr-x     1 root       root            18481 2010-02-28 03:20 .w3m*
-?????????     ? ?          ?                   ?                ? .Xauthority

[/FONT]
Although the source partition is clean and *not* mounted, the target image seems to be corrupted. In [this thread]("http://ubuntuforums.org/archive/index.php/t-1285560.html") I found the hint with fschecking the target image. I did it, and it is also corrupted.

Can anybody please tell me where to look? I have no idea why this does not work... 

Thanks in advance!

Reinhard.

---

### Post by 2hot6ft2 on 2010-04-27
[http://www.clonezilla.org/](http://www.clonezilla.org/)
you can do it over a network as well and people really like it.

---

### Post by dcstar on 2010-04-28
> **czerwinski1977 said:**
> Hi there,

I am desperately trying to make an image of a partition from my old notebook (openSUSE/ext3) via LAN.

Since I am short on external media, I do a dump of the partition via network from the source PC:
```
dd if=/dev/sda1 bs=512 count=55777680 |ssh rm@192.168.1.1 "**cat** >/home/rm/temp/sda1_file"
```
.........

I seriously doubt that a program designed to process ASCII is going to work well with binary input.

---

### Post by Grenage on 2010-04-28
Also, can't you use "of=xxxxx" across SSH, I'm sure I have in the past.

---

### Post by czerwinski1977 on 2010-04-30
Hello again :)

> I seriously doubt that a program designed to process ASCII is going to work well with binary input.
Not true. cat is *not* designed for ASCII. It works for general purposes.

> Also, can't you use "of=xxxxx" across SSH, I'm sure I have in the past.
I'm not sure if I understand you right. You mean i should pipe to a dd in the ssh session.... well this could also have worked.

SOLUTION:
The problem was a bad block on the source disk. Since I had the dd option conv=noerror, dd continued after the bad block but without leaving a respective gap in the target file - this, of course, screwed up the file system.
I then used dd with the option conv=noerror,sync which leaves zeroes for bad data. Everything just fine :)

Thank you all for all your responses!

Reinhard.

---

### Post by babajc on 2011-12-21
> **2hot6ft2 said:**
> [http://www.clonezilla.org/](http://www.clonezilla.org/)
you can do it over a network as well and people really like it.

All well and good, but I took the OP to say this source device was mounted.

From the clonezilla page:
•Online imaging/cloning is not implemented yet. The partition to be imaged or cloned has to be unmounted.

---

