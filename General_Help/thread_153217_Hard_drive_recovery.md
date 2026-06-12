---
title: "Hard drive recovery"
date: 2006-03-31
forum: General Help
---

### Post by kurakusan on 2006-03-31
I need to recover a hard drive that has valuable information but doesn't appear to have any visible partitions.
I have gone to synaptic and installed TestDisk, which I would like to run but I have no clue how to do that.

---

### Post by Prospero2006 on 2006-03-31
You need to be more specific. 
When you say it doesn't have any visible paritions, how do you know that? 
What did you use to determine that?

What I would do:
   -Download slackware install disc 1
   -At the prompt type cfdisk.

   -Download knoppix Live CD
   -See if it shows up there
  
   -Research the 'dd' command and dump what you can
    to a different hard drive.

          -Just a few suggestions. 
              Pros

---

### Post by kurakusan on 2006-03-31
I checked it out with /etc/ftab and a bunch of hard drive utilities. The secton that says where the partions are is gone.

---

### Post by aysiu on 2006-03-31
My quick little test journey for testdisk: ```
user@ubuntu:~$ sudo apt-get install testdisk
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libntfs5
The following NEW packages will be installed:
  libntfs5 testdisk
0 upgraded, 2 newly installed, 0 to remove and 66 not upgraded.
Need to get 439kB of archives.
After unpacking 1270kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com breezy/main libntfs5 1.9.4-2 [60.2kB]
Get:2 http://archive.ubuntu.com breezy/universe testdisk 5.8-1 [379kB]
Fetched 439kB in 4s (99.7kB/s)

Preconfiguring packages ...
Selecting previously deselected package libntfs5.
(Reading database ... 85260 files and directories currently installed.)
Unpacking libntfs5 (from .../libntfs5_1.9.4-2_i386.deb) ...
Selecting previously deselected package testdisk.
Unpacking testdisk (from .../testdisk_5.8-1_i386.deb) ...
Setting up libntfs5 (1.9.4-2) ...

Setting up testdisk (5.8-1) ...
user@ubuntu:~$ testdisk
TestDisk 5.8, Data Recovery Utility, May 2005
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
Please wait...
No harddisk found
You need to be root to use TestDisk

TestDisk exited normally.
user@ubuntu:~$ sudo testdisk
TestDisk 5.8, Data Recovery Utility, May 2005
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
Please wait...
Disk /dev/hda - CHS 38792 16 63 - 19092 MB, sector size=512

TestDisk need 25 lines to work.
Please enlarge the terminal and restart TestDisk.
TestDisk exited normally.
user@ubuntu:~$ sudo testdisk
TestDisk 5.8, Data Recovery Utility, May 2005
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
Please wait...
Disk /dev/hda - CHS 38792 16 63 - 19092 MB, sector size=512

TestDisk exited normally.
user@ubuntu:~$
``` So, apparently, the command you're looking for is *sudo testdisk*, and you want your terminal screen maximized.

---

### Post by kurakusan on 2006-03-31
The hard drive is visible, I've stried using a live cd version of beatrix to see If I can do anything. its ntfs formatted and I put it in a Pc running win98. it didn't even see the drive. I need to use a Hard drive recovery program, but I am really new to linux and 

long story short Im about to defenestrate my comp!!! ](*,) (to defenestrate is to throw out the window)

---

### Post by irw on 2006-03-31
I had a problem where Windows corrupted my partition table.

TestDisk did the job - but only when I downloaded an installed an up-to date version.
I spent hours messing around with a knoppix CD with no success.  The newest version sorted out the problem in less than 2 minutes!


(That was the nail in windows' coffin - now almost full-time Ubuntu only!)

---

### Post by kurakusan on 2006-03-31
wow I think its working.....     this is the happiest I think Ive been all week!!!! Thank you very much
:p :p :p :p :p :p :lol: :lol:

---

### Post by kurakusan on 2006-03-31
What shoudl I set up the partition on the drive I just saved as. It defalts to primary/bootable but since it only has data on it shouldn't it be a logical or something?

---

### Post by NeghVar on 2006-03-31
no that should be fine, it wont actually boot off of it, it will auto boot ubuntu, assuming you have nothing else.

---

