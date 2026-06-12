---
title: "A few important questions before my first install..."
date: 2010-01-12
forum: General Help
---

### Post by BA_UO on 2010-01-12
Hi all, 

As you can see, I am a first time poster, but I have been aggressively browsing the forums and trying to take in as much information as possible for the last little while, and decided it was time to join the community.

I am planning on soon installing ubuntu and dual booting it alongside vista.

Here are a few questions I have before going through the process:

1. How serious/permanent is partioning my disk, or in other words, can I totally screw my whole system if I follow the steps on the Live CD and use a little common sense? (Is it easy to get rid of ubuntu if I decide I don't want it on my computer and dedicate the whole disk to vista once again?)

2. I have read a few posts and web pages about this but cannot get a straight answer.

If I am in windows, can I read files from linux? For example, if I make a .doc file in windows, can I open it when I am logged into ubuntu? (Im also curious about vice versa, if I am logged into linux, can I open a .doc file that I have saved in windows?)

3.  Is dedicating 20GB to my new ubuntu installation enough? Or what are good/ideal partioning sizes for me? 

Background: 
-some basic java/visual basic programming skills.
-competent with Windows OS and applications

Specs:
Model: HP Pavillion dv6000
Processor: AMD athlon(tm) 64 X2 Dual Core Processor TK53 1.7
Ram: 894 MB
System type: 32-bit operation system
Hard Drive: 140GB (about 93 GB free right now)

If you need any other info, or if I was not clear enough in my questions, just let me know.  

Thank you all for your time. 

BA

---

### Post by bodhi.zazen on 2010-01-12
> **BA_UO said:**
> Hi all, 

As you can see, I am a first time poster, but I have been aggressively browsing the forums and trying to take in as much information as possible for the last little while, and decided it was time to join the community.

I am planning on soon installing ubuntu and dual booting it alongside vista.

Welcome, dive right in ...

> Here are a few questions I have before going through the process:

1. How serious/permanent is partioning my disk, or in other words, can I totally screw my whole system if I follow the steps on the Live CD and use a little common sense? (Is it easy to get rid of ubuntu if I decide I don't want it on my computer and dedicate the whole disk to vista once again?)Although RARE, partitioning a hard drive does carry some risk, This is mitigated by backing up and data you do not wish to loose off the hard drive.

> 2. I have read a few posts and web pages about this but cannot get a straight answer.

If I am in windows, can I read files from linux? For example, if I make a .doc file in windows, can I open it when I am logged into ubuntu? (Im also curious about vice versa, if I am logged into linux, can I open a .doc file that I have saved in windows?)Ubuntu uses open office which can open and save microsoft documents. You can install open office in Windows (as well as firefox) if you wish to try it.

You can access your Windows partition from Ubuntu.

> 3.  Is dedicating 20GB to my new ubuntu installation enough? Or what are good/ideal partioning sizes for me? You will need 2 partitions.

1. for swap, size = RAM X 2, I usually say 1 GB max, or Swap == ram if you hibernate or suspend.

2. for root or / , 10 Gb is often more then enough.

---

### Post by michy99 on 2010-01-12
To add to question 2, Ubuntu is able to see and read your Windows partiton, but it might be a problem reading your Ubuntu partition from Windows. There are windows drivers which allow you to access ext2 and ext3 partitions from Windows, but the newest Ubuntu uses ext4 by default, and there are not any windows drivers yet for ext4.

What many people do is set up a NTFS data partition for files which are shared by both Windows and Ubuntu (pictures, documents, videos, music, etc.)

---

### Post by 73ckn797 on 2010-01-12
There is a program called "ext2fs" that can be installed in Windows to read a Ubuntu/Linux partition. I typically can only read the ext2 or ext3 file system. I personnally would not recommend using the default ext4 file system with the latest Ubuntu 9.10. I have lost 3 hard drives this year which, I believe, was due to the ext4 formatting. 2 of the drives were less than 6 months old and were fine until using ext4. Others will disagree about the ext4 file system.

---

### Post by BA_UO on 2010-01-12
Thank you all for the quick replies...

You say I will need 2 partitions...will the partitioner on the Live CD prompt me to do this?

---

### Post by 73ckn797 on 2010-01-12
> **BA_UO said:**
> Thank you all for the quick replies...

You say I will need 2 partitions...will the partitioner on the Live CD prompt me to do this?

The installation steps will suggest several options. Look through each of those carefully before deciding. If there is only one disk to be used and it has Windows on it, it will suggest installing and a dual boot from the same drive or completely wiping the drive and installing Ubuntu only. You hold the key to what happens. If you have 2 drives you can choose to install to that one. I recommend first that you defrag the Windows drive before beginning the installation.

If you have other questions and find searching using the forum search feature less than satisfactory, you can go to [http://www.uboontu.com](http://www.uboontu.com) where it will return Ubuntu specific results. Most results will be forum threads. You can search using phrases just like Google.

---

### Post by BA_UO on 2010-01-12
Thanks, it seems like a handy site!

---

