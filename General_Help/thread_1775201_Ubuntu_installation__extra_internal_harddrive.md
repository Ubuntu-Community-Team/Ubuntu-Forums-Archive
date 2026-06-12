---
title: "Ubuntu installation  extra internal harddrive"
date: 2011-06-04
forum: General Help
---

### Post by Eastwood1 on 2011-06-04
I have Ubuntu installed in VMPlayer on my C drive (1 Terrabyte) with all my other software programs. I have WINDOWS 7.  My G drive is a 80 Gig competely empty internal harddisc.
Can I install it on the G drive?
Which version of Ubuntu?
Do I make a CD from the Internet to Install ubuntu?
Would appreciate any help.
Thank you

---

### Post by Joe- on 2011-06-04
So you want to put Ubuntu on a separate HD rather than run it as a virtual machine?
How did you install Ubuntu onto the VM?

---

### Post by jamesisin on 2011-06-04
If you intend to install Ubuntu on an unused hdd in your current system, you'll likely have a good experience installing using the live cd.  You can use the included partition editor to install Ubu on that entire drive, though the drive lettering Windows uses is meaningless outside of Windows.  Just make certain you are choosing the correct drive when you make your installation choices.  This won't likely be difficult because the installer should be able to tell you the size of each available drive, the formatting or not of each available drive, and which operating system if any is present on each available drive.

---

### Post by Joe- on 2011-06-04
Download Ubuntu Live CD and burn it to a disc. Restart your machine and put the live CD and make sure the PC boots into the live CD not Win7. Follow the on-screen instructions and select the G drive for Ubuntu. :)

---

### Post by oldfred on 2011-06-04
Good advice in above posts.

Herman has a lot of detail and screenshots, not as complex as it may seem just because he explains so much.
Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by Eastwood1 on 2011-06-04
> **Joe- said:**
> So you want to put Ubuntu on a separate HD rather than run it as a virtual machine?
How did you install Ubuntu onto the VM?
 It was done by the IT friend who sold me the computer. It is brand new. He thought that the instal. on the VM was enough needed. I want it totally independent from Microsoft. Hopefully one day get away from MS!

---

### Post by Joe- on 2011-06-04
I suggest then you download Ubuntu Live CD (follow the instructions on the website) and then install Ubuntu to the other hard drive.

---

### Post by oldfred on 2011-06-04
A few more links if you have not partitioned. I recommend partitioning in advance, but you can do it as part of the install.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by Eastwood1 on 2011-06-05
> **oldfred said:**
> A few more links if you have not partitioned. I recommend partitioning in advance, but you can do it as part of the install.
 
Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
 
Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
 
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical
 
Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
 
Thanks for Advice
Will do and report back!
Regards

---

