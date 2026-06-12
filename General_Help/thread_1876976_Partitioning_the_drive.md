---
title: "Partitioning the drive"
date: 2011-11-07
forum: General Help
---

### Post by Aeric Wintershard on 2011-11-07
First of all, I'd like to say hi to everyone, since this is my first post.
Okay, so, my question, as you can read from the title, would be about partitioning.

I have recently installed Ubuntu 11.10, and my goal was to make it run alongside Windows 7. You know, at least until I get familiar with the new environment. :)
Upon installation I was asked to setup my partitions, and since when I was installing Win7 I had no clue I would be installing Ubuntu, I reserved all of the HDD space for Wndows. Apparently, somewhere I went terribly wrong, and the only system that boots up is Ubuntu. Ubuntu can still detect what was my D:\ partition, however, it can not do anything with it, except for copying the stuff from it.

Now, my question is this:
I have a 500.1GB HDD, I need to run both Win7 and Ubuntu on my laptop.
I need at least 80GB on my C:\ partition, and I will separate 3GB for my Swap drive. That leaves me with 417GB of free space. How much is the minimum space requirement for Ubuntu to be installed and run properly, and how much is recommended (also, when Ubuntu installs something, does it install it in its system partition, or somewhere else? If else, then where?*)? The remaining free space will be ntfs, and used for storage as my D:\ partition.

*If I make a second ext4 partition, will Ubuntu be able to detect/read/write to/from it, and can I direct Ubuntu to install to it? (If possible)


Well that would be all for now, and I hope I'm not too demanding for someone who is writing his first post. If I am, feel free to tell me so, if not, expect to hear more from me again! :D:D

PS: If the aforementioned partitioning setup is too complicated, a step by step guide would be appreciated. (And I mean, really step by step, with explanations as to why everything is done as it is done, because I'd actually like to try and understand it.)

Best regards, and thanks again!

---

### Post by Basher101 on 2011-11-07
First of all, ALWAYS install Windows first. Then you can go inside Windows, Defrag and clean the disk and shrink the volume from there. After you done the maximum shrinking (should be about 50% of the total) you can then bootup the Live CD (USB) and startup Gparted. Then shrink Windows until you got it small enough. 

Next is Ubuntu. Now since linux is not very picky, you can install it EVERYWHERE you want, whether on a 4GB usb stick or an external HDD or even on Logical partitions. As for the size, 10 GB for linux alone should be enough, even with some applications. The programs are installed to /usr as i know...but you can split up your install directories for example: partition 1 is your /boot /etc and /home then on partition 2 is your /usr and the rest....you can easily place the directories wherever you want. Also wise decision on the big NTFS storage. I have a 500GB shared NTFS storage for all my Music, videos, documents and downloads which Windows and linux both use.

---

### Post by BillyBoa on 2011-11-07
About the space needed for Ubuntu depends on what you are going to do. I have a 500G HDD and I use 470G for Windows and 30G for Ubuntu. I stored everything in the Win NTFS part and almost nothing to Ubuntu part. So I have access to my files on NTFS because Linux recognizes NTFS but Win is not recognizing Ext4. And I can reinstall any new Ubuntu version anytime, without even having to do a backup.

---

### Post by Gatemaze on 2011-11-07
Welcome to the forum. I have a similar situation like you in some of my systems. I usually have the following partition table:

Primary partition 1: Windows (as much as you need, as it is not easily changed in the future with this configuration)

Extended partition 2.1: / (ext4) about 10 GB should be enough, depending on programs (e.g. if you want full matlab then add another 5GB)
Extended partition 2.2: /shared which is ntfs and much as you want
Extended partition 2.3: /home (ext3) the remaining. Better a separate partition so if you need to upgrade in the future it would be so much easier.

Primary partition 3: Swap (if ram > 2GB about the same size, if less then twice the size of ram)


In this way if I decide I need to give more space to my / then I can resize the /shared (a risky operation but so far I've been lucky :) Weakness you won't be able to resize the windows partition without destroying the extended ones. Unless you create another primary partition between the windows and the linux partitions and also use it as share. Remember you can have up to 4 primary partitions.

---

### Post by westie457 on 2011-11-07
Hi attached is a screenshot of my current HDD. This is a setup that works for me. The largest partition is for data only and can be used by both operating systems. The small (10GB) one is for when I sell /pass the laptop on and can reset it to Factory Default.

One thing to remember when resizing the Windows partition, Windows is greedy and will not allow you to shrink it by as much as you would like to. To shrink it further use Gparted from a LiveCD to get Windows down to the size you want. Once that operation has finished, reboot your computer and allow Windows to run CHKDSK. This will cut down any problems in the future. Also do not move the start point of the Windows partition, this will probably cause a lot of hassle for you to the point of making Windows unbootable.

Hope this helps.

---

### Post by Aeric Wintershard on 2011-11-07
Thanks everyone, that certainly cleared up some of the confusion. However, one new thing arises, when I create a second ext4 partition to be used for /home, do I have to declare it during the setup by setting 'Mount point : /home'?
I also have one more question for westie: The sda4 partition is the one your Ubuntu is installed on, right?

---

### Post by Gatemaze on 2011-11-07
> **Aeric Wintershard said:**
> Thanks everyone, that certainly cleared up some of the confusion. However, one new thing arises, when I create a second ext4 partition to be used for /home, do I have to declare it during the setup by setting 'Mount point : /home'?

Yes

---

### Post by westie457 on 2011-11-07
> **Aeric Wintershard said:**
> I also have one more question for westie: The sda4 partition is the one your Ubuntu is installed on, right?

Hi, no. The SDA4 partition is the extended one, SDA5 has the install and SDA6 is the swap.

---

