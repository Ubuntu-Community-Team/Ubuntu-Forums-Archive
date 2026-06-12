---
title: "Cannot find ntfs partitions"
date: 2010-03-19
forum: General Help
---

### Post by Diptansu on 2010-03-19
I am using jaunty.

I have it installed in a 80 GB ext3 HDD. (This is sdb)

I have another 500 GB. Its NTFS. (This is sda)

It has 3 partitions. Download, Movies, Dump.

They are probably sda1, sda2 and sda3 respectively.

Few days ago when I was using intrepid, all three partitions were showing in the Places menu. But I was being able to mount Movies and Dump. Not the Download one. It was continuously saying 'unable to mount'.

Now, after fresh installation of jaunty (not upgraded from intrepid) only Download partition is showing in the Places menu. There is no option for the other two partitions. 

Help me out please .. :(

---

### Post by plucky on 2010-03-19
> **Diptansu said:**
> I am using jaunty.

I have it installed in a 80 GB ext3 HDD. (This is sdb)

I have another 500 GB. Its NTFS. (This is sda)

It has 3 partitions. Download, Movies, Dump.

They are probably sda1, sda2 and sda3 respectively.

Few days ago when I was using intrepid, all three partitions were showing in the Places menu. But I was being able to mount Movies and Dump. Not the Download one. It was continuously saying 'unable to mount'.

Now, after fresh installation of jaunty (not upgraded from intrepid) only Download partition is showing in the Places menu. There is no option for the other two partitions. 

Help me out please .. :(

Try booting windows and running chkdsk on the NTFS partitions.Linux won't mount an NTFS partition if it hasn't been dismounted properly when windows shuts down.

Good Luck

---

### Post by Diptansu on 2010-03-19
Ah ! .. probably thats the reason .. :( .. last time my windows crashed .. and I went for ubuntu entirely .. So right now I dont have windows .. only ubuntu is here .. 

So I have to install a fresh copy of windows now .. : / .. downer .. :(

---

### Post by plucky on 2010-03-19
> **Diptansu said:**
> Ah ! .. probably thats the reason .. :( .. last time my windows crashed .. and I went for ubuntu entirely .. So right now I dont have windows .. only ubuntu is here .. 

So I have to install a fresh copy of windows now .. : / .. downer .. :(

If you don't have windows,why use NTFS.Perhaps it is a good time to switch over to a linux filesystem.


Good Luck

---

### Post by Diptansu on 2010-03-19
Actually this 500 GB contains tons of data .. and it is already in NTFS format .. so to make it into another format I have to take back up all those data .. 

1) Is ext formats (ext3 I have) are better (by speed or in any means) than the NTFS file system?

2) If I attach my 500 GB ntfs in my friends comp (which has windows) and then shut it down properly .. then again attach it in my comp will it work?

---

### Post by plucky on 2010-03-19
> **Diptansu said:**
> Actually this 500 GB contains tons of data .. and it is already in NTFS format .. so to make it into another format I have to take back up all those data .. 

1) Is ext formats (ext3 I have) are better (by speed or in any means) than the NTFS file system?

2) If I attach my 500 GB ntfs in my friends comp (which has windows) and then shut it down properly .. then again attach it in my comp will it work?

1) The problem is,without windows you don't have a means to repair the NTFS file system.

2) If it is a windows system,you can run chkdsk on the drive and it should then work on linux as long as it is dismounted correctly.

---

### Post by Diptansu on 2010-03-19
hmm .. I think I hvn't been able to make my first question clear .. I just wanted to know ..

1) As a file format is 'ext' performance wise better than 'ntfs'?

I will surely give it a try in my frnds comp .. give you feedback soon .. :)

---

### Post by srs5694 on 2010-03-19
In Linux, ext*fs is likely to perform better than NTFS; however, I don't have pointers to specific benchmarks and I don't recall the details of how much better Linux-native filesystems will perform. This isn't to say that NTFS is a poor-performing filesystem; it's just that the *Linux implementations* of these filesystems are such that Linux performance is likely to be better with Linux-native filesystems.

Another thought about regaining access to the files: If you've got a Windows installation or recovery CD/DVD, you may be able to boot it to do the job, even if Windows isn't installed on the computer.

---

### Post by Diptansu on 2010-03-19
Thanks plucky and srs5694 for your help ..

I do have have a windows installation CD but dont think it has the option to boot live from that .. well .. I will surely give it a look ..

---

### Post by srs5694 on 2010-03-19
> **Diptansu said:**
> I do have have a windows installation CD but dont think it has the option to boot live from that .. well .. I will surely give it a look ..

AFAIK, all Windows install CDs and DVDs since Windows XP (and some in the NT line before that) are bootable. They won't boot to a live desktop, but they can be used for maintenance and recovery operations, including running CHKDSK for disk repairs.

FWIW, there *is* a way to create a bootable Windows system that boots to a (rather limited) desktop with the Windows user interface; check out [BartPE.](http://www.nu2.nu/pebuilder/) You'll need a Windows XP disc to do this. I *think* it can be created in Linux, without Windows actually installed, but I'm not 100% positive of that.

---

