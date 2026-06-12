---
title: "Ntfs hdd"
date: 2010-07-27
forum: General Help
---

### Post by Kay Lukas on 2010-07-27
I just installed Ubuntu 10.04 LTS x64 on my computer. This also the first time I'm working with a linux distribution, so I'm sorry if I don't understand everything.

Yesterday Ubuntu was running perfectly. Today I tried to install nvidia driver, and after that I started rythmbox. That was the moment I noticed my computer wouldn't mount NTFS drives anymore. What is weird cause yesterday it did mount them, and I didn't change anything (atleast I think I don't). 
The exact error Message is:

**Unable to mount location**

Not authorized.

So I searched the internet and they said to other people they should check System>Administration>Users and groups.

So I did check it and it said account type: custom, when I clicked on the button change, which was next to it, It didn't do a thing.

So can you guys help me with this? I really want to try Ubuntu instead of windows.

---

### Post by CharlesA on 2010-07-27
Are you mounting it from the places menu?

Also, are you logged in remotely or at the physical machine?

---

### Post by Kay Lukas on 2010-07-27
> **CharlesA said:**
> Are you mounting it from the places menu?

Also, are you logged in remotely or at the physical machine?
I mounted it from places and from the computer menu. I'm logged in at the physical machine.

---

### Post by CharlesA on 2010-07-27
Try this from a terminal (Applications > Accessories > Terminal) then:

```
sudo fisk -l
```

and post the output please.

---

### Post by Kay Lukas on 2010-07-27
> **CharlesA said:**
> Try this from a terminal (Applications > Accessories > Terminal) then:

```
sudo fisk -l
```and post the output please.
sudo: fisk: command not found

sudo -l gives
Matching Defaults entries for kay on this host:
    env_reset

User kay may run the following commands on this host:
    (ALL) ALL

---

### Post by CharlesA on 2010-07-27
Bah. Sorry, I mistyped.

It should be:

```
sudo fdisk -l
```

---

### Post by Kay Lukas on 2010-07-27
> **CharlesA said:**
> Bah. Sorry, I mistyped.

It should be:

```
sudo fdisk -l
```
```
kay@kay-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb42eb42e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61438976    7  HPFS/NTFS
/dev/sda2            7650       30400   182747407+   f  W95 Ext'd (LBA)
/dev/sda5            7650       30400   182746438+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb1d4b1d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5100    40965718+  83  Linux
/dev/sdb2            5101       19456   115314539+   f  W95 Ext'd (LBA)
/dev/sdb5            5101       19456   115314538+   7  HPFS/NTFS

```

---

### Post by CharlesA on 2010-07-27
So you are trying to mount the 250GB drive?

Are you dual booting with 2 different hard drives?

---

### Post by Kay Lukas on 2010-07-27
> **CharlesA said:**
> So you are trying to mount the 250GB drive?

Are you dual booting with 2 different hard drives?
Its currently dual booting, but I'm going to turn it off because my vista is completely f*cked up, actually can't remember on what hdd vista was, but i reckon its in the dual boot screen so I'm going to check that. I'm trying to mount both the ntfs partitions of the 250gb hdd and the 160 gb hdd, none seem to work. Only the linux partition works.

---

### Post by Kay Lukas on 2010-07-27
Nevermind, the reboot fixed it.

Still wondering why this time it did work but the 5 reboots previously didn't do a thing, but this one did.

I'm feeling like a complete noob now :(

---

### Post by CharlesA on 2010-07-27
Interesting. I wonder what was wrong with it.

Did you do an update recently?

EDIT: Don't forget to mark the thread as solved from the thread tools menu. :)

---

### Post by Kay Lukas on 2010-07-27
> **CharlesA said:**
> Interesting. I wonder what was wrong with it.

Did you do an update recently?

EDIT: Don't forget to mark the thread as solved from the thread tools menu. :)
I did, but after the update I did reboot. But i didn't reboot after I kicked WINE of my system, but then again, before I installed WINE my hdd were already malfunctioning.

---

### Post by CharlesA on 2010-07-27
Very strange indeed. Glad it's working now. :)

---

### Post by Kay Lukas on 2010-07-27
> **CharlesA said:**
> Very strange indeed. Glad it's working now. :)
Yeah, thank you for the help

---

