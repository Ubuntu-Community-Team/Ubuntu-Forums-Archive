---
title: "problem with installation"
date: 2010-07-29
forum: General Help
---

### Post by jokes_finder on 2010-07-29
Hello, guys!

well, I have used Ubuntu 9.10 for a week and I liked it.

The problem is: ubuntu 10.04 setup wizard totally formatted my hard disk!!

well, in step 4 of 7: i chose the the second choice, i.e. erase and use the entire disk and after installation i didn't find the partitions!!

for summarizing:
1- What is meant by the free space on the computer? Does it mean a free partition? What if there's not any free space?

2- I used wubi.exe to install Ubuntu 9.10 from the windows - before using ubuntu 10.04 -, and any of these problems occured.. but instead, i was allowed to choose which partition for Ubuntu and the volume i want for it.

3- what's sda, sdb, ..?

Thanks in advance..
- sry for my bad English -

---

### Post by jokes_finder on 2010-07-29
Really guys, i need help with that..

---

### Post by roger_1960 on 2010-07-29
Hi

It sounds like the 10.4 install did what you asked, ie erase and use the whole disk.  It should have deleted everything (windows & 9.04) as part of the installation process.  The 2nd option install is not like a wubi install.  Does 10.4 work?

sda and sdb etc are the drives detected in your PC.

You probably now have 2 partitions, a ext4 partition and a swap partition.

---

### Post by jokes_finder on 2010-07-29
That's not what i meant
when i was chose the second choice, i was noted that the OS will be deleted.
nothing said that the whole HDD will be deleted!!!

and yeah, 10.04 works well.

look! to re-phrase my problem:

The problem: Ubuntu 10.04 setup wizard totally formatted my entire hard  disk!!

Description: I installed ubuntu 10.04 from the bootable USB stick  (instead of the CD)
                  In step 4 0f 7: I chose the second choice i.e. erase  and use the entire disk
                  And after installation I didn't find the partitions!!!
                  All the hard disk was "filesystem"

Direct questions:

1- I had used ubuntu 9.10 before 10.04, and installed 9.10 using  wubi.exe from the windows, and any of these problems didn't occur.. but  instead, the setup wizard allowed me to choose which partition and the  volume i want for ubuntu. Why didn't this happen while using the  bootable USB stick?

2- Is there a way to re-partition the HDD before installing ubuntu like  what happens when installing windows?

I added the second question..

---

### Post by roger_1960 on 2010-07-29
I think what you were trying to do was upgrade 9.10 to 10.4 rather than install 10.4  The option you chose, erase and use entire disk did just that.  Other options (I cant remember the numbers) allow you to use gparted to modify partitioning before installation.  Other options allow you to install alongside existing OSes?  If you had done that, you would have had Windows, 9.10 and 10.4 installed.

Hopefully you had everything backed up before doing this?

---

### Post by jokes_finder on 2010-07-29
unfortunately, i didn't back up a thing. :(

What about the second question?
Is there a way to re-partition the HDD before installation? as we do when installing windows..

---

### Post by 3rdalbum on 2010-07-29
> **jokes_finder said:**
> unfortunately, i didn't back up a thing. :(

What about the second question?
Is there a way to re-partition the HDD before installation? as we do when installing windows..

Yes, you can create your partitions before booting the Ubuntu CD or before starting the installer, if you wish. Then tell the installer that you want to "Specify partitions manually", and tell it what mount points you want to use for each partition (basically "/", swap, and maybe "/home").

Alternatively, at this step you can create your partitions just as you would in a modern Windows installation.

Telling the Ubuntu installer to erase the entire disk will tend to erase the entire disk.

---

### Post by dreamsR4living on 2010-07-29
> Yes, you can create your partitions before booting the Ubuntu CD or before starting the installer, if you wish. Then tell the installer that you want to "Specify partitions manually", and tell it what mount points you want to use for each partition (basically "/", swap, and maybe "/home").

See the installation manual for more information;

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

And more info about the specifying partitions manually;

[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)

---

### Post by jokes_finder on 2010-07-29
oh! Thanks guys..
and special thanks to dreamsR4living - solved the case! -

---

