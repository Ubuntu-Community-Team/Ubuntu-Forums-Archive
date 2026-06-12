---
title: "unmountable LuksContainer after Raid5 resize"
date: 2010-01-08
forum: General Help
---

### Post by chri7 on 2010-01-08
Hi Folks,

I used a raid 5 of 5*1TB via Kernel raid on md0.
I then created a luks out of md0 -> /dev/mapper/md0.
I formated ext3 this container.

That worked fine. Now I baught another Harddrive and grew the raid to now 6 Devices. The Raid is now running und bigger than before - great.

The luksOpen still works BUT i can't mount the ext3 on it.
It seems like the luks Volume also grew, it's now 1TB bigger without doing anything ...

The Problem: I can't mount the luks anymore, mapping it was no big deal so.. Always tells me that I should specify the filesystem type: 
```

root@ubuntu:/home/ubuntu# mount /dev/mapper/md0 /mnt/tmp
mount: Sie müssen den Dateisystemtyp angeben

```

If I do is then it continues to give me errors:

```

root@ubuntu:/home/ubuntu# mount /dev/mapper/md0 /mnt/tmp -t ext3
mount: wrong fs type, bad option, bad superblock on /dev/mapper/md0,
       missing codepage or helper program, or other error
       Manchmal liefert das Syslog wertvolle Informationen – versuchen
       Sie  dmesg | tail  oder so

```

Any suggestions what to do .. It seams as if the luks system doesnt know that the luks container isn't using the whole drive

---

### Post by chri7 on 2010-01-08
I am just trying testdisk to check the /dev/mapper/md0 device ...

that looks like it takes days ... but so far i got this 

```

Disk /dev/mapper/md0 - 5804 GB / 5405 GiB - CHS 2746780411 1 1
Analyse cylinder 655656/2746780410: 00%


 ext3                         128 30978303671 30978303544
 ext3                       52734 24873647293 24873594560


```

Isn'T that goog news so far?

---

### Post by chri7 on 2010-01-08
*arg* I just screwed up completele, never be too lazy when acting as root ...

I thought, after lots of trys with ext3 rescue, to try chkfsck.xfs on the /dev/mapper/md0 device ... I dunno why but I typed mkfs.xfs ... so all fried now !!!

Well ... last backup was last year - bad thing ;P

---

