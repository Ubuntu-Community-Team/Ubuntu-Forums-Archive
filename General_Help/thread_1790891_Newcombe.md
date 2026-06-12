---
title: "Newcombe"
date: 2011-06-25
forum: General Help
---

### Post by Newcombe on 2011-06-25
I'm trying to use xubuntu as my home server.  I have two 2TB hard drives and I'm trying to get access the second one.  How would I go about doing so?

---

### Post by Ozymandias_117 on 2011-06-25
I'm not sure I understand the question; Have you opened your file browser and clicked on the drive and it won't mount? Are you trying to get it to automatically mount somewhere during boot? What is the drive formatted as?

---

### Post by Newcombe on 2011-06-26
I haven't formatted it as anything and I'm not sure I know what you mean by mount!  (I've only been using ubuntu and xubuntu for about two weeks, so I'm new to all of this!)  I have both drives connected to the motherboard correctly but I don't know if there's a certain way to make it accessible.

I guess what I'm trying to figure out is how do I access my second hard drive?

---

### Post by keithpeter on 2011-06-26
Hello Newcombe

Try opening a terminal (in the launcher at the bottom of the screen if you are using 11.04, its the fourth icon from the end)

In the terminal, you can type commands. Try typing 

```
df -m
``` 

and see what output you get. Copy and paste the output here and the output will tell us if your drive is already there. Mine looks like this...

```

keith@quiet:~$ df -m
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sda1                12045      5656      5778  50% /
none                       938         1       937   1% /dev
none                       943         2       942   1% /dev/shm
none                       943         1       943   1% /var/run
none                       943         0       943   0% /var/lock
/dev/sda5               213524    117400     85278  58% /home
/dev/sdc1                 1884         1      1884   1% /media/NO_NAME

```

I only have one internal hard drive, but it is split into several partitions (/dev/sda1 &c) and I have an SC card with my photos in the card reader (that one is /dev/sdc1).

---

### Post by Yellow Pasque on 2011-06-26
If you haven't formatted it, then start with:
```
gksu gparted
```

---

### Post by Newcombe on 2011-06-26
@Keith here's what I got,

newcombe@Frank:~$ df -m
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sdb2              1875779     29892   1750603   2% /
none                       999         1       998   1% /dev
none                      1006         1      1005   1% /dev/shm
none                      1006         1      1005   1% /var/run
none                      1006         0      1006   0% /var/lock


So I'm guessing my second partition has not been formatted yet!?

---

### Post by keithpeter on 2011-06-26
> **Newcombe said:**
> @Keith here's what I got,

newcombe@Frank:~$ df -m
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sdb2              1875779     29892   1750603   2% /
none                       999         1       998   1% /dev
none                      1006         1      1005   1% /dev/shm
none                      1006         1      1005   1% /var/run
none                      1006         0      1006   0% /var/lock


So I'm guessing my second partition has not been formatted yet!?

Hello Newcombe

Yup, looks like you should follow the advice of Temüjin. Is that a second partition or a second physical drive? Either way, you need to look at what gparted shows you.

Cheers

---

### Post by WorMzy on 2011-06-26
You're guessing? I would hope you *know* whether your second disk is partitioned+formatted or not. ;)

We can't tell anything from that output, I'm not sure why Keith asked for it. Run

```
sudo fdisk -l
```

and post the output here.

---

### Post by keithpeter on 2011-06-26
> **WorMzy said:**
> You're guessing? I would hope you *know* whether your second disk is partitioned+formatted or not. ;)

We can't tell anything from that output, I'm not sure why Keith asked for it. Run

```
sudo fdisk -l
```

and post the output here.

@WorMzy

That was my next idea. I thought that the second drive may have been allocated during installation.

@Newcombe

Try WorMzy's commands in your terminal and see what they show

---

### Post by Newcombe on 2011-06-26
Here's what it returns;

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0004826b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243202  1953513472    5  Extended

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953514583+  ee  GPT

---

### Post by WorMzy on 2011-06-26
Okay, there's no usable partition on your second disk (sda), but there is an empty extended partition which fills the entire disk (that's fine). You can create usable partitions (ext4 would arguably be the best choice if you only plan on using Linux on your machine) in the extended partition by using gparted.

Follow the instructions Temüjin gave you to launch gparted. From there, the interface is pretty self explanatory. You'll need to create at least one usable partition on the disk before you can use it for anything.

---

