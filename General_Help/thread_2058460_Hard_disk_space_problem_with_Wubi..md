---
title: "Hard disk space problem with Wubi."
date: 2012-09-15
forum: General Help
---

### Post by jnLink on 2012-09-15
So I'm on a PC with dual boot Windows XP and Ubuntu 12.04, and I know that i have at LEAST 10 gigabytes of RAM. I can access it when I get on XP. But on Ubuntu it says at bottom of home folder that I have 192 MB. Please help me. :c I couldn't find help anywhere else on the Interwebs. :(

---

### Post by oldos2er on 2012-09-15
Are you talking about hard disk space (not [RAM]("http://en.wikipedia.org/wiki/RAM"))? Did you install Ubuntu into its own partition or use the Windows installer Wubi?

When running Ubuntu, can you run these two commands in a terminal and copy and paste all the output here? ```
sudo fdisk -l

df -h
```

---

### Post by jnLink on 2012-09-15
jon@ubuntu:~$ sudo fdisk -l
[sudo] password for jon: 

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe4651a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78156224    39078081    7  HPFS/NTFS/exFAT
jon@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0      4.7G  4.3G  152M  97% /
udev            367M  4.0K  367M   1% /dev
tmpfs           150M  852K  149M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            374M   80K  374M   1% /run/shm
/dev/sda1        38G   19G   19G  51% /host
/dev/sr1         34M   34M     0 100% /media/disk
jon@ubuntu:~$

---

### Post by steeldriver on 2012-09-15
You appear to be running a WUBI installation (Ubuntu is in a loop file within windows) with 4.7GB of disk space allocated to the Ubuntu filesystem - almost all of it used

[http://askubuntu.com/questions/107470/how-can-i-check-how-much-space-there-is-left-on-wubi-versus-how-much-space-it-ta](http://askubuntu.com/questions/107470/how-can-i-check-how-much-space-there-is-left-on-wubi-versus-how-much-space-it-ta)

As oldos2er has already said, this has nothing to do with memory (RAM)

---

### Post by jnLink on 2012-09-15
Is there a way that I can tap into the space on my Windows C:/?

---

### Post by dcstar on 2012-09-16
> **jnLink said:**
> Is there a way that I can tap into the space on my Windows C:/?

Reinstall and use 10GB this time.

---

### Post by oldos2er on 2012-09-16
Changed thread title to be more accurate.

---

### Post by Mark Phelps on 2012-09-16
> **jnLink said:**
> Is there a way that I can tap into the space on my Windows C:/?

According to the info posted, you only have one partition on the drive.  Wubi installs into a file INSIDE that partition.  When it reports space, that space is of the file system INSIDE that file -- not the remainder of the partition.

Look at the Wubi Guide linked below, section 8.12:

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by jnLink on 2012-09-17
I got it :3 23 gigs of space now. HUZZAH

---

### Post by Mark Phelps on 2012-09-17
Great -- so please use the thread tags to mark this thread as SOLVED. thanks

---

