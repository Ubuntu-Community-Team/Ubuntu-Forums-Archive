---
title: "Help on using Unbuntu live cd to repair a Corrupted Xp registry"
date: 2006-04-07
forum: General Help
---

### Post by quik77 on 2006-04-07
Hi all not sure if this is the right place but I'm hoping someone here knows how to do this:

I have an Xp Home edition pc that my boss wanted me to upgrade at the office.

on rebooting from running windows update, I got windows/system32/config/system is missing error message (registry is corrupt)

using the xp cd and recovery console Bootcfg cannot find a windows installation, and chkdsk /p/r on the HD finishes normally

I can't get bootcfg, bootfix or fixmbr to work, it can't find the xp installation at all.

so I want to use the live cd, enable read/write to ntfs and take the registry backups from an old restore point and put them in the right place so I can get it to boot.  

If anyone has some clues or can point me in the right direction many thanks ^^

---

### Post by aysiu on 2006-04-07
XP is probably NTFS.
Read/write could make it worse than it is now.
Are you willing to take that risk?

---

### Post by quik77 on 2006-04-07
right now I got nothing else to be done, I've tried all the recovery console options, tried to do the inplaces install of windows, but It will not find the previous installation... and Since the system isn't mine its my Boss's daughters I can't rellay wipe the whole thing like I'd like to  (to give you an idea of the family they all use AOL highspeed and each computer I've looked at of thiers has had >500  spyware hits)

going to try and see what unbuntu can see right now live cd is runnign atm.. worst comes to worst if my best bet is the new install I'll do it other problem is if it asks for a win xp key.. cause its my personal copy of xp.. not the one for the actual installed one, I grabbed it from home when everythign went pear shaped.

maybe I'll jsut go home play WOW all weekend and get my boss to bring the from home stuff monday >.<

---

### Post by aysiu on 2006-04-07
Maybe you can boot the live CD, download [the NTFS-Fuse .rpm](http://prdownloads.sourceforge.net/linux-ntfs/ntfsprogs-fuse-1.13.0-1.i586.rpm) and then ```
cd Desktop
sudo apt-get update
sudo apt-get install alien
sudo alien -i ntfsprogs-fuse-1.13.0-1.i586.rpm
```

---

### Post by quik77 on 2006-04-07
Ok trying this now

---

### Post by bscbrit on 2006-04-07
Just a thought - why not use the Ubuntu live CD to make a backup of all of the user's data (files, pictures etc) and then do a clean install of XP?  It will work faster than it did before, you can clean off all of the c**p and spyware, and you will have a working system.  You will need to make a note of all of the drivers and make sure that your Boss has all of the original disks (perhaps even the recovery disk issued when he bought the computer???) so that software programs can be re-installed.  Failing that, you could always try to convert him to Ubuntu!

Or is your Boss using illegal software?.....

---

### Post by quik77 on 2006-04-07
going to try that too if i can't just un lobotomize the registry...  still requires his cds from home though and he's left for the day.. hmm brain fart  whats the fast way to mount the windows drives when I'm runnign the live cd? I forgot again.

---

### Post by aysiu on 2006-04-07
[QUOTE=quik77]whats the fast way to mount the windows drives when I'm runnign the live cd? I forgot again.[/QUOTE] Use Knoppix.

If you're stuck with a Ubuntu live CD, try this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by quik77 on 2006-04-11
ok things are gettign strange now.. it will boot the unbuntu live cd, It will Not boot the Knoppix live cd.  trying to redownload and burn the knoppix cd now at work.

also guess I should of mentioned this before, this is a dell computer so the windows on it is probabley oem.. >.<  lurking in the dell forums now so far found 1 person with the exact same problems as me...

ubuntu@ubuntu:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

is the error message i get when i try and mount the windows partition

---

