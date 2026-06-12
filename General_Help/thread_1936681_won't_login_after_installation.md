---
title: "won't login after installation"
date: 2012-03-06
forum: General Help
---

### Post by lubi on 2012-03-06
ok, so i installed Lubuntu 11.10 desktop on my hard drive (not using wubi).
and after full installation and restarting, login screen shows and not accepting my username and password. i am 100% sure i use correct username and pass and i watch for capslock.
then i pressed crtl+alt+F1 opened terminal and after entering username and pass this message appears:
*-bash cannot create temp file for here-document: no space left on device*
so i entered "df -h" and here's what it shows me:
filesystem dev/sda2
size          9.9G
used         9.7G
avail         0
use%        100%
mounted    on

it is freshly installed lubuntu, there is no way it can be 9.7GB big. partition i installed lubuntu on is 10GB big.
partition wizard in my windows XP also shows me that that partition is 97% full :(
heres screenshot:
[IMG]http://oi40.tinypic.com/2m5jm1e.jpg[/IMG]

---

### Post by JC Cheloven on 2012-03-06
> **lubi said:**
> somebody has to know, i'm trying to install it for days. same thing happens when trying to install ubuntu

If it also happens when trying to install regular Ubuntu, chances are that something is wrong with the filesystem in that partition. You could boot from live and try ```
sudo fsck /dev/sda2
``` (assuming your 10 Gb partition is sda2, please check before, for example using the sudo fdisk -l command).

--> But I'd start by simply launching a live session, erasing the partition, and re-creating it. You can use gparted for that. Then installing Lubuntu, Ubuntu, or whatever, likely from the same live session.

Hope that helps.

EDIT: btw, not specially important, but you didn't set up any swap, did you?

---

### Post by ankspo71 on 2012-03-06
> 
it is freshly installed lubuntu, there is no way it can be 9.7GB big
There is one possibility...If something existed on that partition before you installed Lubuntu, and the partition didn't get reformatted before or during the installation, then there is a chance the installation could end up being that large.

---

### Post by raja.genupula on 2012-03-07
are you able to login from terminal ? 
i mean with this ctrl+alt+F1

---

### Post by lubi on 2012-03-07
> **JC Cheloven said:**
> If it also happens when trying to install regular Ubuntu, chances are that something is wrong with the filesystem in that partition. You could boot from live and try ```
sudo fsck /dev/sda2
``` (assuming your 10 Gb partition is sda2, please check before, for example using the sudo fdisk -l command).

--> But I'd start by simply launching a live session, erasing the partition, and re-creating it. You can use gparted for that. Then installing Lubuntu, Ubuntu, or whatever, likely from the same live session.

Hope that helps.

EDIT: btw, not specially important, but you didn't set up any swap, did you?

sudo fsck /dev/sda2    gives me:
fsck from util-linux 2.10.1
e2fsck 1.41.14 (22-dec-2010)
/dev/sda2: clean, 112771/658368 files, 2564605/2632960 blocks
that is my 10 GB partition lubuntu is on, btw i dont know what these numbers means. and yes, i didn't make any swap this time. but when i make swap (1GB) same thing happens.

> **ankspo71 said:**
> There is one possibility...If something existed on that partition before you installed Lubuntu, and the partition didn't get reformatted before or during the installation, then there is a chance the installation could end up being that large.

i created that partition manually in windows in program partition wizard and i formated it after creation. it is ext4 partition,  funny thing also after formatting, shows me that 312MB is used so i suppose that is some system files or something because formatting can't erase it.

> **raja.genupula said:**
> are you able to login from terminal ? 
i mean with this ctrl+alt+F1

when i press crtl+alt+F1 terminal shows, asking for login, i enter, then asking for password, i enter then message appears
-bash cannot create temp file for here-document: no space left on device

---

### Post by JC Cheloven on 2012-03-07
> **lubi said:**
> sudo fsck /dev/sda2    gives me:
fsck from util-linux 2.10.1
e2fsck 1.41.14 (22-dec-2010)
/dev/sda2: clean, 112771/658368 files, 2564605/2632960 blocks
that is my 10 GB partition lubuntu is on 
Ok, it looks healthy. The disk seems to be actually full. Have you tried to simply navigate that partition from the live session, to see what files are packing your disk?

> i created that partition manually in windows in program partition wizard and i formated it after creation. it is ext4 partition,
as far as I remember, windows wasn't good at all managing linux partitions. I'd better use a linux tool for that, again from live.

>   funny thing also after formatting, shows me that 312MB is used so i suppose that is some system files or something because formatting can't erase it.
It's normal. Usually some space is reserved for system use, so that the operating system can write on the disk (for control purposes and such) even if it becomes apparently full.

---

