---
title: "question about installing Ubuntu on a Windows-installed computer"
date: 2012-06-11
forum: General Help
---

### Post by subjugater on 2012-06-11
I have a new laptop with windows 7 already installed by the manufacture. I plan to install 64-bit Ubuntu on it to have both Windows 7 and Ubuntu. My questions are:

1. I can install directly without re-partitioning the disk and re-installing Windows 7 in a newly-partitioned and newly-formated location, right?

2. Is there anything to which I should use caution either during the installation of Ubuntu on a Windows-installed computer or in the future?

Forgive me if these dumb questions have been posted for many times before. If so, please kindly refer me to those threads. (I searched but didn't find threads with questions exactly the same as what I am asking.)

Thanks very much, folks.

---

### Post by VE6EFR on 2012-06-11
Here is a very good guide that should help to get you up and running in no time:

[http://www.liberiangeek.net/2012/04/dual-boot-windows-7-and-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/dual-boot-windows-7-and-ubuntu-12-04-precise-pangolin/)

---

### Post by Mark Phelps on 2012-06-11
> **subjugater said:**
> I have a new laptop with windows 7 already installed by the manufacture. I plan to install 64-bit Ubuntu on it to have both Windows 7 and Ubuntu. My questions are:

1. I can install directly without re-partitioning the disk and re-installing Windows 7 in a newly-partitioned and newly-formated location, right?
WRONG. You don't need to reinstall Win7, but you do need to perform manual partitioning. Read more below ...

> 2. Is there anything to which I should use caution either during the installation of Ubuntu on a Windows-installed computer or in the future?..

YES ... Read more below ...

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by HermanAB on 2012-06-11
Well, bear in mind that partitioning and dual booting works, but is really very 20th century.

The better way to do it (unless you use Windows to play games), is to install Linux on the machine, then install Virtualbox and make a Windows virtual machine.  Then you can run Windows in a window, concurrently with Linux.  This is an altogether better solution since you can then simultaneously run Linux and Windows applications.  I do this every day on my netbook and laptop machines.

---

### Post by forrestcupp on 2012-06-11
What??? He just said he has a computer with Win7. There's no evidence that he's maxed out his partitions.

It's not nearly as complicated as people are making it sound. Assuming you *don't* have the maximum allowed primary partitions, you don't have to do anything at all to prepare ahead of time, other than to back up your important files in case something gets screwed up (usually by human error). The Ubuntu installation will give you the option to install Ubuntu alongside of Windows 7, and you can choose how much space you want to dedicate to both. Then it will automatically do all of the repartitioning and resizing for you. There are other options to do all of this manually, but you don't have to do it that way. You can choose the automated way included in the installation if you want.

Of course, if you *have* already created the maximum allowed primary partitions, then you'll have to manually do some of the things already mentioned. But you would probably know it if that is the case.

> **HermanAB said:**
> Well, bear in mind that partitioning and dual booting works, but is really very 20th century.

The better way to do it (unless you use Windows to play games), is to install Linux on the machine, then install Virtualbox and make a Windows virtual machine.  Then you can run Windows in a window, concurrently with Linux.  This is an altogether better solution since you can then simultaneously run Linux and Windows applications.  I do this every day on my netbook and laptop machines.Virtual machines are great, but they're not the solution for everyone. That's why we still have dual booting. Virtual machines use virtual hardware, which is not nearly as powerful as installing to your real hardware. If you're into gaming at all, then VMs are definitely *not* the answer. But you already mentioned that. :)

---

### Post by subjugater on 2012-06-11
> **VE6EFR said:**
> Here is a very good guide that should help to get you up and running in no time:

[http://www.liberiangeek.net/2012/04/dual-boot-windows-7-and-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/dual-boot-windows-7-and-ubuntu-12-04-precise-pangolin/)

Thanks so much, buddy.

---

### Post by subjugater on 2012-06-11
> **HermanAB said:**
> Well, bear in mind that partitioning and dual booting works, but is really very 20th century.

The better way to do it (unless you use Windows to play games), is to install Linux on the machine, then install Virtualbox and make a Windows virtual machine.  Then you can run Windows in a window, concurrently with Linux.  This is an altogether better solution since you can then simultaneously run Linux and Windows applications.  I do this every day on my netbook and laptop machines.

Thanks for your comments. My questions:

1. By "Virtualbox", do you mean wine? Or something else?
2. I use Windows only for Windows Office Suite (word, powerpoint, excel, etc) and MATLAB. (I know that LibreOffice/OpenOffice are the surrogates, but sometimes when I submit my resume in some on-line job application system, these systems are not well-designed and complain quite often.) Can I use real Windows Office and MATLAB in the Virtualbox? 

Thanks!

---

### Post by subjugater on 2012-06-11
> **forrestcupp said:**
> What??? He just said he has a computer with Win7. There's no evidence that he's maxed out his partitions.

It's not nearly as complicated as people are making it sound. Assuming you *don't* have the maximum allowed primary partitions, you don't have to do anything at all to prepare ahead of time, other than to back up your important files in case something gets screwed up (usually by human error). The Ubuntu installation will give you the option to install Ubuntu alongside of Windows 7, and you can choose how much space you want to dedicate to both. Then it will automatically do all of the repartitioning and resizing for you. There are other options to do all of this manually, but you don't have to do it that way. You can choose the automated way included in the installation if you want.

Of course, if you *have* already created the maximum allowed primary partitions, then you'll have to manually do some of the things already mentioned. But you would probably know it if that is the case.

Virtual machines are great, but they're not the solution for everyone. That's why we still have dual booting. Virtual machines use virtual hardware, which is not nearly as powerful as installing to your real hardware. If you're into gaming at all, then VMs are definitely *not* the answer. But you already mentioned that. :)

Thanks so much for your input. But I am a bit of confused:

1. Which one on earth should I use to shrink the size of the partition on which Windows 7 is installed? Windows computer management or Ubuntu installation process?

2. My understanding is that the entire hard disk has to be divided into two independent parts, on each of which a system is (or will be) installed. Am I right? In other words, the two systems do not share the whole disk and each of them only rules its own domain, right?

3. What is the limitation of a virtual windows machine? Which virtual machine is the best/most popular one? Wine?

4.Can I view and modify files in one system from the other? Can I just move files from one to the other? 

Forgive me if my questions are naive. I really intend to know these. Thanks so much anyway.

---

### Post by oldfred on 2012-06-11
The instructions in the first link only show one Windows partition. That is very unusual now. The default install of Windows 7 is two partitions - a hidden 100MB boot/repair partition and the main install. Then the Vendor uses two partitions - one is the recovery partition and another for "tools". That way you cannot easily isntall  anything else, Microsoft is happy and the vendor does not get calls its help desk cannot manage.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

Basically use Windows tools for Windows and Linux tools for Linux. So use Windows to shrink the Windows partition and gparted to create (or the installer) to create partitions. Or if just a basic install, you can choose to install into the unallocated & the install automatically decides what to do. I prefer some control so I always partition in advance.

I have not used any virtual systems. On my short list to try, but I basically prefer dual boot. Virtual will be a bit slower as you are sharing resources where dual boot requries you to shutdown and reboot, but then each system has all memory & cpu to use.

Ubuntu can read & write NTFS partitions. Windows will not read Linux formated partitions. Also Windows often does not like too much data written into the system partition by foreign systems, so best to create a d: or NTFS data partition for any data you might want in both systems. Even though I do not boot XP, I still have Firefox profile, Thunderbird profile and all photos for Picasa in a shared NTFS partition.

---

### Post by Scott Baker on 2012-06-11
I have to ask this, because no else has. Why do you want to install Ubuntu on your machine? I know this sounds strange, but if you have a working machine, why do you want to diddle with it? If you're not comfortable with re-partitioning your hard drive, this is NOT the time to try to start learning. The fine folks here in the forums can help walk you through this task, but one small boo-boo can lead to a whole lot of headaches. Think carefully about why you want to do this, and how important it is to do. If you still say yes, then come on back and give us a shout. There are SEVERAL ways to do this, and someone will point you in the right direction.

---

### Post by forrestcupp on 2012-06-11
I must have a lot different experience than everyone else. I've never bothered to repartition beforehand. The Ubuntu installer is made to automate all of this and make it easy for you. That's part of the whole point of the installer's ease of use. I've never had any problem with Windows having trouble with its partition being resized by GParted or the Ubuntu installer. It might scan the disk, but it didn't end up having any problems.

> **Scott Baker said:**
> If you're not comfortable with re-partitioning your hard drive, this is NOT the time to try to start learning.
When is the right time? You have to start somewhere.

It's really *a lot* easier than people seem to be making it.

---

### Post by subjugater on 2012-06-11
> **Scott Baker said:**
> I have to ask this, because no else has. Why do you want to install Ubuntu on your machine? I know this sounds strange, but if you have a working machine, why do you want to diddle with it? If you're not comfortable with re-partitioning your hard drive, this is NOT the time to try to start learning. The fine folks here in the forums can help walk you through this task, but one small boo-boo can lead to a whole lot of headaches. Think carefully about why you want to do this, and how important it is to do. If you still say yes, then come on back and give us a shout. There are SEVERAL ways to do this, and someone will point you in the right direction.

I am a computational mathematician who did a lot of numerical simulation/scientific computing using Linux. It will be extremely inconvenient if I call FFTW, LAPACK, BLAS, OpenFOAM in Windows. And the clusters I used for parallel computing are all in Linux. So no wonder that I want to use Linux on my local machine. Does this make sense to you?

---

### Post by subjugater on 2012-06-11
> **forrestcupp said:**
> I must have a lot different experience than everyone else. I've never bothered to repartition beforehand. The Ubuntu installer is made to automate all of this and make it easy for you. That's part of the whole point of the installer's ease of use. I've never had any problem with Windows having trouble with its partition being resized by GParted or the Ubuntu installer. It might scan the disk, but it didn't end up having any problems.


When is the right time? You have to start somewhere.

It's really *a lot* easier than people seem to be making it.

My friend, thank you for your advice and making me not to fear that much.

---

