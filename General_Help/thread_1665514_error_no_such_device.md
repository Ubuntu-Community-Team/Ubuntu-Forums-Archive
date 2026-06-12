---
title: "error: no such device"
date: 2011-01-12
forum: General Help
---

### Post by mugginbun on 2011-01-12
Hi there! I've just installed ubuntu 10.04.1 amd 64 from windows xp using wubi. After doing some updates (One of them to grub) ubuntu asked me to reboot. Upon reboot I was greeted with:
> error: no such device: 2971fb2b-0355-4b26-9132-7b001c9ad97b
grub rescue>
And I seem to be stuck here. I would appreciate help very much!

Thanks in advance!

---

### Post by bcbc on 2011-01-12
You need to install the windows bootloader. You were 'tricked' into replacing it with grub. See Problem #1 of the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198").

Note: you only need to fix the MBR - on XP it's "fixmbr". Ignore any additionaly instructions e.g. to fix the bootsector (fixboot).

---

### Post by mugginbun on 2011-01-13
I've encountered a bit of a problem!
When I run:
> sudo apt-get install lilo

I get:
> 
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
 mbr
Suggested packages:
 lilo-doc
The following NEW packages will be installed:
 lil mbr
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 415kB of archives.
After this operation, 1,331kB of additional disk space will be used.
Do you want to continue [Y/n]?Y
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main mbr 1.1.10-2
 Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main lilo 1:22.8-8ubuntu1
 Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mbr/mbr](http://archive.ubuntu.com/ubuntu/pool/main/m/mbr/mbr) 1.1.10-2_amd64.deb Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/lilo/lilo_22.8-8ubuntu1](http://archive.ubuntu.com/ubuntu/pool/main/l/lilo/lilo_22.8-8ubuntu1) amd64.deb Could not resolve 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix missing?


I'm very unsure of what to do and further help would be very much appreciated!

---

### Post by bcbc on 2011-01-13
> **mugginbun said:**
> I've encountered a bit of a problem!
When I run:


I get:


I'm very unsure of what to do and further help would be very much appreciated!

Try it again. Maybe there was a problem accessing the repository. Or change your repository. (Make sure you're connected to the internet.)

> The following NEW packages will be installed:
  lilo
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 390kB of archives.
After this operation, 1,221kB of additional disk space will be used.
Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/main lilo 1:22.8-8ubuntu1 [390kB]
Fetched 390kB in 2s (139kB/s)                           
Preconfiguring packages ...
Selecting previously deselected package lilo.
(Reading database ... 187683 files and directories currently installed.)
Unpacking lilo (from .../lilo_1%3a22.8-8ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up lilo (1:22.8-8ubuntu1) ...


---

