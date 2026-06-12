---
title: "swap partition &quot;problem.&quot;"
date: 2010-12-09
forum: General Help
---

### Post by ninjaaron on 2010-12-09
Hey. I installed Jolicloud on my computer for a little while, but I had a problem, so I took it off. In the process of repartitioning (from live USB) I deleted my swap space, so I made a new swap partition, right?

Anyway, on reboot, I checked my system monitor and it said had 0.0 gigs of swap. Now, I don't recall that I've ever actually used all of my system ram, 3GB, though maybe when I wasn't looking (I have encoded a video or two in my day).

In any event, do I even need swap memory? If so, how to I get it back?

---

### Post by WlaadDyaab on 2010-12-09
[http://www.faqs.org/docs/Linux-mini/Partition.html](http://www.faqs.org/docs/Linux-mini/Partition.html)

I'm actually reading it myself just now

I hope it's of any use

---

### Post by tredegar on 2010-12-09
Check the entry for your swap partition in **/etc/fstab**

The UUID of the swap partition will have changed when you created a new one, and **fstab** probably has the old one, so the new partition cannot be mounted as swap.

**sudo blkid** will tell you what the UUIDs of your partitions are, so you can tell which UUID should relate to swap in **fstab**

---

### Post by tajiknomi on 2010-12-09
[SIZE=2]If your swap partition is made already and it isn't mounting/swapon, then their must be missing entry of swap in your /etc/fstab
you can add a simple line for swap in fstab , the line is something like this:-


[/SIZE]```
[SIZE=3]#Entry for /dev/sda7
UUID=31d375a6-05be-4873-a867-d6acb273ec89    none    swap    sw    0    0[/SIZE]
```[SIZE=2]In the above line, the swap is present on ***/dev/sda7*** , and you can find out your UUID from :-

[/SIZE]```
[SIZE=3]sudo blkid[/SIZE]
```[SIZE=2]Good luck[/SIZE] :p

---

### Post by ninjaaron on 2010-12-09
ok, I opened /etc/fstab.

These are the lines that were not commented:
```
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
```

(and there were no comments between them either).

This is what I got from blkid:
```
/dev/sda2: LABEL="/dev/sda2" UUID="e37ce1bc-f78f-464b-aff3-960465936278" TYPE="swap" 
/dev/sda1: UUID="18af7fb6-f162-4fe4-abf8-07f9225b610a" TYPE="ext4"
```

I'm gonna just try to comment out the line for /dev/sda5, and add a line that looks just like it for /dev/sda2... trying now...

---

### Post by ninjaaron on 2010-12-09
well, that did it.

thanks guys.

---

### Post by tredegar on 2010-12-09
Yes, where **fstab** says sda5 it chould be changed to sda2
Then **sudo swapon -a** will restart swap

---

### Post by tajiknomi on 2010-12-09
[SIZE=2]you can mark ***thread-as-solved ***in ***thread-tool*** above[/SIZE]..:p

---

### Post by ninjaaron on 2010-12-09
> **tredegar said:**
> Yes, where **fstab** says sda5 it chould be changed to sda2
Then **sudo swapon -a** will restart swap ah... I just did a reboot.

> **tajiknomi said:**
> [SIZE=2]you can mark ***thread-as-solved ***in ***thread-tool*** above[/SIZE]..:p

I always wondered how to do that. :D
(seriously though)

---

