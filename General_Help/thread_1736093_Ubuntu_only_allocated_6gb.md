---
title: "Ubuntu only allocated 6gb ??"
date: 2011-04-22
forum: General Help
---

### Post by ddude117 on 2011-04-22
I installed Ubuntu 10.10 using wubi.exe from windows 7 . Windows seven is still installed and so is ubuntu but ubuntu is only allocated about 6 gb of hard drive space and i dont know how to allocate it the entrie hard drive

---

### Post by DanneStrat on 2011-04-22
> **ddude117 said:**
> I installed Ubuntu 10.10 using wubi.exe from windows 7 . Windows seven is still installed and so is ubuntu but ubuntu is only allocated about 6 gb of hard drive space and i dont know how to allocate it the entrie hard drive

Wubi is meant for dual-booting windows and ubuntu.

I think the maximum disk space you can give ubuntu from wubi

is about 30 GB. If you were able to give ubuntu all disk space 

then windows wouldn't have any space left to run on.

You could of course resize your virtual disk by following this guide:

[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)


If you want to get rid of windows entirely

you need to either migrate your wubi install to real partitions 

or install from live cd.

Look at the section "How do I migrate to a real partition, and/or get rid of Windows entirely?" in this guide:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by ddude117 on 2011-04-22
seth@ubuntu:~$ sudo bash /home/seth/wubi-move-2.0.sh /dev/sda 

/home/seth/wubi-move-2.0.sh: Partition /dev/sda could not be mounted for validation.
/home/seth/wubi-move-2.0.sh: This is normal if the partition is unformatted or the file
/home/seth/wubi-move-2.0.sh: system is corrupted. It could also mean you have entered
/home/seth/wubi-move-2.0.sh: the wrong partition. The partition will have to be formatted
/home/seth/wubi-move-2.0.sh: in order to complete validation.
/home/seth/wubi-move-2.0.sh: PLEASE MAKE SURE YOU HAVE SELECTED THE CORRECT PARTITION.
/home/seth/wubi-move-2.0.sh: Please close all open files before continuing.
/home/seth/wubi-move-2.0.sh: About to format the target partition (/dev/sda).
/home/seth/wubi-move-2.0.sh: Proceed with format (Y/N)

??
this came up in terminal . (I'll add the swap later)  ive only got one partition with windows 7 on it .. ^^ Will this replace it with my ubuntu installed via wubi

---

### Post by DanneStrat on 2011-04-22
> **ddude117 said:**
> seth@ubuntu:~$ sudo bash /home/seth/wubi-move-2.0.sh /dev/sda 

/home/seth/wubi-move-2.0.sh: Partition /dev/sda could not be mounted for validation.
/home/seth/wubi-move-2.0.sh: This is normal if the partition is unformatted or the file
/home/seth/wubi-move-2.0.sh: system is corrupted. It could also mean you have entered
/home/seth/wubi-move-2.0.sh: the wrong partition. The partition will have to be formatted
/home/seth/wubi-move-2.0.sh: in order to complete validation.
/home/seth/wubi-move-2.0.sh: PLEASE MAKE SURE YOU HAVE SELECTED THE CORRECT PARTITION.
/home/seth/wubi-move-2.0.sh: Please close all open files before continuing.
/home/seth/wubi-move-2.0.sh: About to format the target partition (/dev/sda).
/home/seth/wubi-move-2.0.sh: Proceed with format (Y/N)

??
this came up in terminal . (I'll add the swap later)  ive only got one partition with windows 7 on it .. ^^ Will this replace it with my ubuntu installed via wubi


You must specify a partition to move to.

First exit that dialogue by pressing "N" for no.

"sda" just means the first harddrive.


If you only have one harddrive and one partition you would do:

```
sudo bash wubi-move-2.0.sh /dev/sda1
```

To specify the first partition.

Then your windows partition will be formatted and ubuntu

will be placed there instead.

If you get any more errors let me know.

---

### Post by ddude117 on 2011-04-22
It said this .. 

```
seth@ubuntu:~$ sudo bash /home/seth/wubi-move-2.0.sh /dev/sda1
/home/seth/wubi-move-2.0.sh: /dev/sda1 is mounted - please unmount and try again
```

What do I do ??

B

---

### Post by ddude117 on 2011-04-22
I tried unmounting it but it said ....

could not unmount /dev/sda1

umount: /host: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))


Im reeeallly stuck

---

### Post by DanneStrat on 2011-04-22
> **ddude117 said:**
> I tried unmounting it but it said ....

could not unmount /dev/sda1

umount: /host: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))


Im reeeallly stuck

If you haven't got any particular reason to keep

you wubi install, I would suggest you boot back to windows

and burn a live cd to install from.

If you don't know how to do that I can help you.

---

### Post by ddude117 on 2011-04-22
I know how i just don't have any cd's or usb's to burn .the reason i wanted to change from windows is causse it had graphic driver/screen resoulution isuues on my pc . aand i knew ubuntu didnt have isuues like that sso i hunted down my old ubuntu install disk but it didnt work so i had to find a way to install it without a disc .. but thanks anyway . :)

---

### Post by dino99 on 2011-04-22
for a real installation, follow this howto:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

wubi is only to see "how it is" not for serious things

---

### Post by ddude117 on 2011-04-22
Yeaah but how do i ut ubuntu onto those paartions only using wubi . cause my windows has unfortunatly crashed

---

### Post by DanneStrat on 2011-04-22
> **ddude117 said:**
> Yeaah but how do i ut ubuntu onto those paartions only using wubi . cause my windows has unfortunatly crashed

Doing a live cd is the recommended way to install ubuntu.

To avoid running into problems, see if you can get some cd's,

or you can borrow a usb-stick to install from.

---

### Post by ddude117 on 2011-04-25
How do I install using flash drive . I managed to borrow one off a friend .

---

