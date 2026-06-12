---
title: "booting from hard disk"
date: 2012-05-06
forum: General Help
---

### Post by Talareño on 2012-05-06
Hello,

Using AA1 i deleted Windows and my old Ubuntu. I am now using Ubuntu only on this computer booting from a pen drive.

I'd like to install it permanently so that I may boot from the hard drive rather than from some removable media. Please help.

Sorry for my lack of technical finesse.

Nick

---

### Post by oldfred on 2012-05-06
Is your USB flash drive the liveCD, so it gives you the option to install?

You can just use the default if the hard drive is unallocated, or use entire drive. That will erase everything.

Or if you want more than the default / (root) & swap you can manually install or Something else.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

---

### Post by Talareño on 2012-05-06
Oldfred,

thanks for the quick reply. i cleaned out the original drive. No more Windows. i guess the USB is the liveCD. Actually I don't see the hard drive. Somewhere I can read that there's some 160 GB disk space available. I don't have a Windows program to work with.

Thanks,

Nick

---

### Post by oldfred on 2012-05-06
Can you open gparted on you install and see the other drive. 

Do you have an install option on the screen/menu of your system?

---

### Post by Talareño on 2012-05-07
no, I can't open gparted and I don't have the install option.

---

### Post by oldfred on 2012-05-07
The standard full install does not include gparted by default as you cannot use it on your working system.
But you can use it on another drive where you can unmount all the partitions, so download gparted.
sudo apt-get install gparted

But you then do not have an install CD or USB version?

---

### Post by Talareño on 2012-05-07
No, I don't. I'd like to get a pendrive version or something. I'm in Japan and would like to get something here rather than have it sent from abroad.

---

### Post by oldfred on 2012-05-07
You can download it. There probably is a local server in Japan.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Talareño on 2012-05-07
I think I'm not making myself clear. I'm writing this on Ubuntu in the place I want it. I'm using a pendrive to run it. I now have nothing but this Ubuntu on my Aspire One. I want to not have to use the pen drive. I want Ubuntu to load straight from the hard drive. In part I find the pendrive too fragile.

thank you,

Nick

---

### Post by codingman on 2012-05-07
If your question has been answered, please set this thread as solved :)

---

### Post by Talareño on 2012-05-09
Codingman.

I have no idea why you would ask that question.

I'm not making myself understood & you want to brush me off.

Bye bye. I'll mark this thread as unsolvable as people wish to just move on and not deal with beginners.

---

### Post by Shadius on 2012-05-09
> **Talareño said:**
> Codingman.

I have no idea why you would ask that question.

I'm not making myself understood & you want to brush me off.

Bye bye. I'll mark this thread as unsolvable as people wish to just move on and not deal with beginners.

The links that oldfred provided will help you. From what I understand, all you're left with is the Ubuntu on your pendrive, correct, and you want to no longer use the pendrive but instead install Ubuntu to a hard disk drive, correct? If so, you'll need to download the Ubuntu ISO and choose the method of installation you prefer, whether by USB Drive or creating a LiveCD. Use the links oldfred has provided you, they have what you need. :)

---

### Post by Talareño on 2012-05-09
Shadius,

You understood correctly. Maybe I just don't know how to go about doing what he suggested. Sorry. I'm not technically advanced enough to understand all the jargon.

---

### Post by Shadius on 2012-05-09
> **Talareño said:**
> Shadius,

You understood correctly. Maybe I just don't know how to go about doing what he suggested. Sorry. I'm not technically advanced enough to understand all the jargon.

As a beginner myself, I understand. I will try to help you as best as I can. I suggest you read the links oldfred provided you and decide which method of installation, whether USB Drive or LiveCD, you prefer before we continue. :)

---

