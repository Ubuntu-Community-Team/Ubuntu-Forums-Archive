---
title: "installing ubuntu"
date: 2012-04-23
forum: General Help
---

### Post by pete44444444 on 2012-04-23
Hello everybody,
I'm fairly new to ubuntu and need help installing it. When I boot from the cd to install there is no option to run ubuntu along side windows xp. It only says I can replace windows or do something else. It also say it detects more than one operating system. I do not understand this because the only os on the computer is windows xp. I previously had ubuntu installed inside of windows just to try if out but I uninstalled it via add or remove programs so I could do a true dual boot.

I know there is a way to install a dual boot under the do something else option but I am completely clueless. Could you please walk me step by step through this process? Remember I need an idiot proof explanation. I have watched numerous youtube videos and read many website posts and searched the forums but I am still very confused.

Thanks,
Pete

---

### Post by kc1di on 2012-04-23
hi Pete,

Welcome to Ubuntu.  below i've link to and install guide that I find quite straight forward. Good Luck and come back and tell us how you make out. 

[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by pete44444444 on 2012-04-23
> **kc1di said:**
> hi Pete,

Welcome to Ubuntu.  below i've link to and install guide that I find quite straight forward. Good Luck and come back and tell us how you make out. 

[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

"When I boot from the cd to install there is no option to run ubuntu along side windows xp. It only says I can replace windows or do something else."

Did you read my post at all? I'm not just posting because I'm too lazy to research it my self. That guide is no help to me because I don't have the option to install along side windows.

---

### Post by kc1di on 2012-04-23
Which .iso did you download?  if it's the wubi one Download the live cd instead.

---

### Post by strask on 2012-04-23
Hi Pete.

Did you resize your windows partition to make space for Ubuntu? If not, the reason you are not getting the option you want may be that there is no space on your disk for ubuntu to install itself without ruining windows.

Most windows computers that I have seen recently come installed with three partitions; the first two are small recovery partitions and the third is the main windows partition that takes up the rest of the disk. The recovery partitions are likely what ubuntu is talking about when it says it sees multiple operating systems.

Generally speaking, the first thing you will need to do is back up all your windows data in case you (or ubuntu) make a mistake and delete something. Then you run a defragmenting tool to move your data to the front of the partition, then you shrink the partition to make some unpartitioned free space on the hard drive.

I'm not a windows xp expert so I am sorry but I don't know the specific commands you need.

---

### Post by jadtech on 2012-04-23
there is a lot of info missing here to get help 

what processor  is it 32bit 64bit
how much ram 
what graphic card
what size is the hard drive 
how much free space and how many primary partitions does it have  

you said you had a wubi install running what version of ubuntu, xubuntu or lubuntu was it  ?? 

you said the live CD detects  2 operating systems  when you were installing last  time did you for some reason even accidently choose to make a partition some how and maybe ubuntu is already there some how even in part ???

---

### Post by pete44444444 on 2012-04-23
> **strask said:**
> Hi Pete.

Did you resize your windows partition to make space for Ubuntu? If not, the reason you are not getting the option you want may be that there is no space on your disk for ubuntu to install itself without ruining windows.

Most windows computers that I have seen recently come installed with three partitions; the first two are small recovery partitions and the third is the main windows partition that takes up the rest of the disk. The recovery partitions are likely what ubuntu is talking about when it says it sees multiple operating systems.

Generally speaking, the first thing you will need to do is back up all your windows data in case you (or ubuntu) make a mistake and delete something. Then you run a defragmenting tool to move your data to the front of the partition, then you shrink the partition to make some unpartitioned free space on the hard drive.

I'm not a windows xp expert so I am sorry but I don't know the specific commands you need.

Can I ":shrink the partition to make some unpartitioned free space on the hard drive" during the ubuntu installation? If so how? I have no idea how to use the partition manager or whatever it is called during the installation.

---

### Post by strask on 2012-04-23
> **pete44444444 said:**
> Can I ":shrink the partition to make some unpartitioned free space on the hard drive" during the ubuntu installation?
No, not without destroying your windows data. The shrinking of the partition is something you need to do from within windows, before you begin the ubuntu install.

---

### Post by jadtech on 2012-04-23
check this link for shrinking  xp volume to make room for linux 

[http://jamesmcdonald.id.au/it-tips/gnu-linux/linux-tools/shrink-your-windows-xp-ntfs-partition-to-half-size-and-install-linux-while-keeping-the-nt-bootloader](http://jamesmcdonald.id.au/it-tips/gnu-linux/linux-tools/shrink-your-windows-xp-ntfs-partition-to-half-size-and-install-linux-while-keeping-the-nt-bootloader)

---

### Post by pete44444444 on 2012-04-23
> **strask said:**
> No, not without destroying your windows data. The shrinking of the partition is something you need to do from within windows, before you begin the ubuntu install.

Where could i find some step by step information on how to do this? Every guide I found on the internet uses the top option to install along side windows and uses the slider bar to say how much hard drive goes to windows and how much goes to ubuntu. I don't understand why I can do this. Why doesn't the option to install along windows show top for me.

---

### Post by strask on 2012-04-23
[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

Just found this. It looks like I was partly wrong and you can use Gparted to do the resizing.

---

### Post by jadtech on 2012-04-23
> **strask said:**
> [https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

Just found this. It looks like I was partly wrong and you can use Gparted to do the resizing.

yes you can there is no real safe way to shrink the volume of window up to vista there is better luck with programs like partition magic if you want to pay for them ..

---

### Post by audiomick on 2012-04-23
Use the windows tool to shrink the windows partition. Remove all the old stuff in the partition first, then defrag it. Shrink it, then start Windows a couple of times and let it do any disk check stuff it wants to do. Then you can go ahead an do your partitioning for your Linux stuff.

Back up anything important before you start.

---

