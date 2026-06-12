---
title: "System shutdown too fast - Filesystem it's not cleanly umounted"
date: 2012-03-10
forum: General Help
---

### Post by StiveKnoxx on 2012-03-10
I'm using ubuntu 11.10 with kernel kernel 3.0.0-16-generic  filesystem is ext4, and, everytime I shutdown, the system shutdown too fast, and with it, the filesystem it's not umounted properly...
So, every-time I start my computer, fsck runs and check the file system, fixes a lot of things, sometime reboot too...

I think this is bad, cause I lost some files sometimes, so, what can I do to try to fix or try to find where the problem is?

Here's my /etc/rc6.d folder:
stive@steinn:/etc/rc6.d$ ls
README  S01networking  S01reboot  S01sendsigs  S01umountfs  S01umountnfs.sh  S01umountroot  S02urandom

Thanks!

---

### Post by matt_symes on 2012-03-10
Hi

> README S01networking S01reboot S01sendsigs S01umountfs S01umountnfs.sh S01umountroot S02urandom

I was just looking at this for you. Your simlinks are different than mine if the above are your symlinks.

```
matthew@matthew-Aspire-7540:~$ ls -l /etc/rc6.d/
total 4
lrwxrwxrwx 1 root root  18 Feb  2 18:13 K01timidity -> ../init.d/timidity
lrwxrwxrwx 1 root root  29 Jan  5 16:44 K10unattended-upgrades -> ../init.d/unattended-upgrades
lrwxrwxrwx 1 root root  14 Jan 23 09:35 K20atop -> ../init.d/atop
lrwxrwxrwx 1 root root  17 Mar  6 18:04 K20postfix -> ../init.d/postfix
lrwxrwxrwx 1 root root  27 Jan  5 16:44 K20speech-dispatcher -> ../init.d/speech-dispatcher
-rw-r--r-- 1 root root 351 Feb 17 05:17 README
lrwxrwxrwx 1 root root  18 Jan  5 16:44 S20sendsigs -> ../init.d/sendsigs
lrwxrwxrwx 1 root root  17 Jan  5 16:44 S30urandom -> ../init.d/urandom
lrwxrwxrwx 1 root root  22 Jan  5 16:44 S31umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx 1 root root  20 Feb 16 23:11 S35networking -> ../init.d/networking
lrwxrwxrwx 1 root root  18 Jan  5 16:44 S40umountfs -> ../init.d/umountfs
lrwxrwxrwx 1 root root  20 Jan 23 23:48 S48cryptdisks -> ../init.d/cryptdisks
lrwxrwxrwx 1 root root  26 Jan 23 23:48 S59cryptdisks-early -> ../init.d/cryptdisks-early
**lrwxrwxrwx 1 root root  20 Jan  5 16:44 S60umountroot -> ../init.d/umountroot**
lrwxrwxrwx 1 root root  16 Jan  5 16:44 S90reboot -> ../init.d/reboot
matthew@matthew-Aspire-7540:~$ 
```

unmountroot unmounts root (funny that). You also may want to check

```
/etc/rc0.d
```

In there are the links to run level 0 (shutdown). Here are mine.

```
matthew@matthew-Aspire-7540:~$ ls -l /etc/rc0.d/
total 4
lrwxrwxrwx 1 root root  18 Feb  2 18:13 K01timidity -> ../init.d/timidity
lrwxrwxrwx 1 root root  29 Jan  5 16:44 K10unattended-upgrades -> ../init.d/unattended-upgrades
lrwxrwxrwx 1 root root  14 Jan 23 09:35 K20atop -> ../init.d/atop
lrwxrwxrwx 1 root root  17 Mar  6 18:04 K20postfix -> ../init.d/postfix
lrwxrwxrwx 1 root root  27 Jan  5 16:44 K20speech-dispatcher -> ../init.d/speech-dispatcher
-rw-r--r-- 1 root root 353 Feb 17 05:17 README
lrwxrwxrwx 1 root root  18 Jan  5 16:44 S20sendsigs -> ../init.d/sendsigs
lrwxrwxrwx 1 root root  17 Jan  5 16:44 S30urandom -> ../init.d/urandom
lrwxrwxrwx 1 root root  22 Jan  5 16:44 S31umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx 1 root root  20 Feb 16 23:11 S35networking -> ../init.d/networking
lrwxrwxrwx 1 root root  18 Jan  5 16:44 S40umountfs -> ../init.d/umountfs
lrwxrwxrwx 1 root root  20 Jan 23 23:48 S48cryptdisks -> ../init.d/cryptdisks
lrwxrwxrwx 1 root root  26 Jan 23 23:48 S59cryptdisks-early -> ../init.d/cryptdisks-early
lrwxrwxrwx 1 root root  20 Jan  5 16:44 **S60umountroot -> ../init.d/umountroot**
lrwxrwxrwx 1 root root  14 Jan  5 16:44 S90halt -> ../init.d/halt
matthew@matthew-Aspire-7540:~$ 
```

IIRC, It does not matter that they start with an S here.

This is on a precise install.

Kind regards

---

### Post by StiveKnoxx on 2012-03-10
That solved!!!!

Thanks for the reply!
Here's my links sequence now:

stive@steinn:/etc/rc6.d$ ls
README  S01networking  S02sendsigs  S03urandom  S04umountnfs.sh  S05umountfs  S06umountroot  S07reboot

Thanks for you help, lost files it's really bad, also fsck making boot slow, not cool too.

---

### Post by matt_symes on 2012-03-10
Hi

> **StiveKnoxx said:**
> That solved!!!!

Thanks for the reply!
Here's my links sequence now:

stive@steinn:/etc/rc6.d$ ls
README  S01networking  S02sendsigs  S03urandom  S04umountnfs.sh  S05umountfs  S06umountroot  S07reboot

Thanks for you help, lost files it's really bad, also fsck making boot slow, not cool too.

I'm glad it's fixed. 

Just a thought; you might want to call networking after umountnfs.sh if you use any networked filing systems.

```
S01sendsigs  S02urandom  **S03umountnfs.sh S04networking** S05umountfs  S06umountroot  S07reboot
```

Kind regards

---

### Post by dcstar on 2012-03-10
The original VMware Player 4.0.0 and Workstation 8 releases seriously broke the order of init files in Ubuntu, this has now been rectified but anyone who installed those original releases will have already damaged their systems.

---

### Post by matt_symes on 2012-03-11
Hi

> **dcstar said:**
> The original VMware Player 4.0.0 and Workstation 8 releases seriously broke the order of init files in Ubuntu, this has now been rectified but anyone who installed those original releases will have already damaged their systems.

Ahhh; so that's how it happened. 

I was wondering how on earth the symlinks could have got so messed up.

Thanks for the info dcstar.

Kind regards

---

### Post by StiveKnoxx on 2012-03-11
Well, actually, I think it was my fault, cause I used BUM (boot up manager) to remove some services (bluetoothd, lighttpd, mysql, postgresql) were the only one removed ...

---

