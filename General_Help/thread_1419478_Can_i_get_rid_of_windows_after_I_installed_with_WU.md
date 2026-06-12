---
title: "Can i get rid of windows after I installed with WUBI?"
date: 2010-03-01
forum: General Help
---

### Post by jeremyleroy96 on 2010-03-01
Hi i have installed ubuntu with WUBI and i was wondering if i could boot into ubuntu and just delete the windows partition and expand? Or is ubuntu dependent on windows because i installed it with WUBI. I have windows 7 build 7100 (beta) 32 bit and ubuntu 9.10 i386 32 bit

---

### Post by switch10 on 2010-03-01
I'm pretty sure you cannot.  It is installed within Windows.  I'd imagine that you could backup your home folder, Install Ubuntu, and then restore your backed up /home folder.

---

### Post by hhh on 2010-03-01
Unless you move Wubi to a dedicated partition with LVPM, Wubi is dependent on Windows (and the Window Master Boot Record) as it is installed onto your Windows partition. And even if you did install Ubuntu to it's own partition, why wouldn't you keep your Windows install too and dual-boot? Please see these links for more info...

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

HTH

---

### Post by chicoharv on 2010-03-01
Yes you can. Yuo can insert your cd and install it as all Ubuntu.  It will change your HD from Fat 32 to Lenux. Be aware that you might want to back up bookmarks, and address books first.

---

### Post by chicoharv on 2010-03-01
I agree, keep a dual boot, get rid of WUBI

---

### Post by lisati on 2010-03-01
> **chicoharv said:**
> Yes you can. Yuo can insert your cd and install it as all Ubuntu.  It will change your HD from Fat 32 to L[COLOR="Red"]i[/COLOR]nux. Be aware that you might want to back up bookmarks, and address books first.

Back up [SIZE="4"]all[/SIZE] your important data first

---

### Post by meierfra. on 2010-03-01
> Hi i have installed ubuntu with WUBI and i was wondering if i could boot into ubuntu and just delete the windows partition and expand?
If Wubi is on a different partition than Windows, you can delete the Windows partition  and keep Wubi (but you would have  to install grub to the MBR beforehand, otherwise you won' t be able   to boot Wubi)

But I'm not sure whether  you will be able to expand     Wubi. You can expand Wubi with [Lubi]("http://lubi.sourceforge.net/lvpm.html"), but that requires  Windows.  

So you have the following option:

[list=1]
[*]  Use Lubi to convert  Wubi  to a regular Ubuntu and then delete  Windows and expand Ubuntu. 

[*]  Install Grub to the MBR, delete Windows and create  a Data partition instead of expanding Wubi

[*]  Backup all your valuable  data, delete Windows and Wubi and install Ubuntu.
[/list]

Option 2  is the easiest. But you still will be running Wubi (so performance is slightly slower and the file system can get corrupted more easily)
If you decide on option 2, let me know and I can show you how to install Grub to the MBR.

But I  would choose options 3, unless  you spend lots of time customizing Wubi.

---

### Post by djchandler on 2010-03-01
> **chicoharv said:**
> Yes you can. Yuo can insert your cd and install it as all Ubuntu.  It will change your HD from Fat 32 to Lenux. Be aware that you might want to back up bookmarks, and address books first.

I believe the OP is asking for a non-destructive method. What you are talking about is a destructive re-partitioning of the hard drive and install from scratch, then restoration of home directory data.

@ jeremyleroy96:

What you are wanting to do requires a complete reinstall of Ubuntu. It will overwrite your current install. Understand the backup and restore process first, and use the same user name and password as in your Wubi installation of Ubuntu in the new hard disk install. If you know what you are doing with all the hidden directories and data in your current home directory and can back up this data to another device (an external HD or thumb drive on the USB port) and know how to restore all that data, then by all means go for it. Just know that you are wiping that hard drive clean in order to do this.

See this answer in this thread.
[http://ubuntuforums.org/showpost.php?p=4835486&postcount=4](http://ubuntuforums.org/showpost.php?p=4835486&postcount=4)

---

### Post by meierfra. on 2010-03-01
> Unless you move Wubi to a dedicated partition with LVPM, Wubi is dependent on Windows (and the Window Master Boot Record) 
Wrong.  Grub2 is  able to boot Wubi without any help from the Window MBR.

> What you are wanting to do requires a complete reinstall of Ubuntu
A complete reinstall might be the best option. But it is not required. Once Wubi is installed, it is completely independent  from the Window operating system. I have personally run Wubi, after deleting Windows and without using LVPM

---

### Post by waynefoutz on 2010-03-02
> **meierfra. said:**
> A complete reinstall might be the best option. But it is not required. Once Wubi is installed, it is completely independent  from the Window operating system. I have personally run Wubi, after deleting Windows and without using LVPM

Why would you do such a thing? You wouldn't be running with a real file system. Wubi is not a partition, it a big single file that Ubuntu thinks is a partition. If that file gets any data corruption, the wubi install gets hosed. A wubi install is meant for testing, for newbies to try out Ubuntu without the commitment that comes along with partitioning your drive. It's not meant to be permanent.

---

### Post by meierfra. on 2010-03-02
> Why would you do such a thing?
I just tried it out in a virtual machine to see whether is it possible. 

Please look at my first post. I clearly pointed out  Wubi's flaws and recommended a fresh install as the best option. But I still see it as my duty to point out all the options, in particular since  various of the claims made in this  thread by other people are plainly wrong.

---

### Post by jeremyleroy96 on 2010-03-02
i would of never used wubi if i knew it done that. The problem is, when i wanted to install Ubuntu normally it made me shrink my windows partition to split it half. I need it to only take up 10 gb right now because windows has too many "unmovable" files! so i have no way to install ubuntu into a SMALL partition without wubi? I have all the data i need off the computer. But i need Ubuntu in a partition that is only 10gb is that possible? But i need windows for another week and then i want to delete it then expand ubuntu. But i now want to do a full install of ubuntu into a small partition 10gb

---

### Post by hhh on 2010-03-02
> **meierfra. said:**
> Wrong.  Grub2 is  able to boot Wubi without any help from the Window MBR.
Where's the documentation on that?

> **meierfra. said:**
> Once Wubi is installed, it is completely independent  from the Window operating system. I have personally run Wubi, after deleting Windows and without using LVPM

Hmm, like I said, that's not what the documentation says. From the FAQ and the Guide...
> How does Wubi work?
[B]
Wubi adds an entry to the Windows boot menu[/B] which allows you to run Linux. **Ubuntu is installed within a file in the Windows file system** (c:\ubuntu\disks\root.disk), this file is seen by Linux as a real hard disk.

> How do I uninstall it?

You uninstall it as any other applications. **In Windows go to the control panel and select "Add or Remove Programs", then select Wubi/Ubuntu and uninstall it.**

> **meierfra. said:**
> ...in particular since  various of the claims made in this  thread by other people are plainly wrong.

*ring ring!!* "Hello, Kettle? This is Pot..."

---

### Post by meierfra. on 2010-03-02
> Where's the documentation on that?
Hardly any of the more advanced features of Grub 2 are documented. That's why I do lots of testing myself and figure out what can be done with Grub2.


> Wubi adds an entry to the Windows boot menu which allows you to run Linux. Ubuntu is installed within a file in the Windows file system (c:\ubuntu\disks\root.disk), this file is seen by Linux as a real hard disk.

I completely agree with these statement and I never claimed otherwise.

The first sentence tells you that Wubi uses the Windows boot loader to boot Wubi. But it does not claim that there is no other way to boot Wubi. 
 I'm personally booting Wubi with Grub 2.

The second sentence tells  you that Wubi is a file in the Window file system.  I never claimed that Wubi is independent from the Windows file system, but it is independent  from the Windows operating system.

> You uninstall it as any other applications. In Windows go to the control panel and select "Add or Remove Programs", then select Wubi/Ubuntu and uninstall it.
So what?
You can delete a regular Ubuntu install  by reformatting or deleting the Ubuntu partition in Windows disk management.  Does that make Ubuntu dependent on the Windows operating system?

---

### Post by Post Monkeh on 2010-03-02
> **jeremyleroy96 said:**
> i would of never used wubi if i knew it done that. The problem is, when i wanted to install Ubuntu normally it made me shrink my windows partition to split it half. I need it to only take up 10 gb right now because windows has too many "unmovable" files! so i have no way to install ubuntu into a SMALL partition without wubi? I have all the data i need off the computer. But i need Ubuntu in a partition that is only 10gb is that possible? But i need windows for another week and then i want to delete it then expand ubuntu. But i now want to do a full install of ubuntu into a small partition 10gb

i personally have never had a problem resizing my windows partitons from linux, but you should really do any ntfs partitioning from windows.

first thing is make sure you have all your data you need from ubuntu backed up. then delete your wubi install.

defrag your hard disk.  now's where it gets tricky. you need to get a partitioning program. windows does have a basic one but i've never used windows 7 so i don't know if it lets you resize. i've used [that]("http://download.cnet.com/Easeus-Partition-Master-Home-Edition/3000-2248_4-10863346.html?tag=mncol") before.

create a partition of whatever size you want, and install ubuntu to it.

you CAN resize your windows partitions from ubuntu, but because of file fragmentation it isn't really recommended.

---

### Post by Mark Phelps on 2010-03-02
> **meierfra. said:**
> Wrong.  Grub2 is  able to boot Wubi without any help from the Window MBR. ... I have personally run Wubi, after deleting Windows and without using LVPM
Wow -- that is impressive!!

Now, if only the folks that maintained (?) the Wubi guide could get around to adding that info, and what additional tweaks are needed to get the thing working with a preinstall Win7 machine -- we would see a massive drop in the "wubi doesn't work" posts on this forum.

---

### Post by jeremyleroy96 on 2010-03-02
i don't need the wubi install i have only had it for a day. So how do i install ubuntu into a 10gb partition? The problem is that windows has some unmovable files and i can not make a partition any bigger then 10gb without my windows going corrupt! 


Edit: I just read i can keep my wubi okay so can i just extend the partition after deleting windows? I might just want to get a working ubuntu but i guess i prefer it to be normal but if wubi will work i have no problem with keeping it as long as there are no disadvantages

---

### Post by djchandler on 2010-03-04
> **Post Monkeh said:**
> i personally have never had a problem resizing my windows partitons from linux, but you should really do any ntfs partitioning from windows.

first thing is make sure you have all your data you need from ubuntu backed up. then delete your wubi install.

defrag your hard disk.  now's where it gets tricky. you need to get a partitioning program. windows does have a basic one but i've never used windows 7 so i don't know if it lets you resize. i've used [that]("http://download.cnet.com/Easeus-Partition-Master-Home-Edition/3000-2248_4-10863346.html?tag=mncol") before.

create a partition of whatever size you want, and install ubuntu to it.

you CAN resize your windows partitions from ubuntu, but because of file fragmentation it isn't really recommended.

The guy who says you can save your Wubi install goes against conventional wisdom. While it may be possible, it doesn't sound like something I would or could do. I've been familiar with Linux for 10 years, and I have been running emulators and such from virtual files systems (which is what the Wubi install does) for even longer. What meierfra is saying is undocumented; even if he's 100% correct, no one else has apparently duplicated what he has done.

I think I can pretty fairly say that I know what I'm doing with disk management. I've been running multiple operating systems from a single hard disk or from multiple disks on a single computer for over 20 years. I have intact data that originally was written to 90 or 180 KB single-sided 5.25" floppy disks that's pushing 30 years old that I can bring up in a matter of a minute or two on one of my computers.

The quotes above from Post Monkeh are the most straightforward advice posted in this thread yet. I have done this with Windows 7 more times than I care to say. But in the past week, I've had Debian 5, OpenSUSE 11.2, a Wubi install of Ubuntu 9.10 and Ubuntu 9.10 installed back on a primary partition. This is just on my laptop with Windows 7, and Windows 7 is still intact. It's had Grub 2, Vista/7 bootloader and now Grub 1 on the MBR in that time too.

Yes, I'm nuts, and have nothing better to do with my time. I even toyed with the idea of installing Gentoo just last night.

Do a disk cleanup and a defrag to free up as much room as possible. Usually the biggest unmovable file in Windows is the swap file. Try turning off virtual memory and reboot before trying to shrink the Windows partition and see if that frees up some room. Windows has a tendency to put that file almost exactly in the middle of any free space the disk actually has. Also delete any system restore files or just turn off System Restore before you do the defrag. After you've turned off Virtual Memory and System Restore, reboot and do a defrag, then see how big that free space can be. Be aware that it's possible to access the Windows NTFS partition(s) of your disk in Ubuntu (using Mount Manager) once Ubuntu is installed.

You can get by with 10GB for an install of Ubuntu. It's not a hog like Windows is for disk space. Follow the advice above. Go to computer management under Administrative Tools, then Disk Management to shrink the Windows partition. Make sure you leave the part of the disk you want to use for Ubuntu as unpartitioned. It should be color coded black and labeled "unallocated." 

The partitioner in Ubiquity (the Ubuntu installer) will give you the option to install Ubuntu in the largest contiguous unused space. That's the option to choose after you have gone to all this trouble. Once you have gotten rid of Windows, Gparted will allow you to enlarge the Ubuntu / partition so you can then use your whole drive later.

I'm guessing you are running the release candidate (Windows 7 RC) that's become a pain. I think it will still run for up to two hours at a time for another 3 months.

[http://technet.microsoft.com/en-us/evalcenter/dd353205.aspx](http://technet.microsoft.com/en-us/evalcenter/dd353205.aspx)

> Watch the calendar: The RC will expire on June 1, 2010. Starting on March 1, 2010, your PC will begin shutting down every two hours. Windows will notify you two weeks before the bi-hourly shutdowns start. To avoid interruption, you&#8217;ll need to install a non-expired version of Windows before March 1, 2010. You&#8217;ll also need to install the programs and data that you want to use.

---

### Post by meierfra. on 2010-03-04
Just for clarification:

1)   If Wubi and the Window OS are on the same partition, one  of course cannot delete that partition without   deleting Wubi. But one can delete all the files on that partition except the Ubuntu directory. 
    
2)  If Wubi and the Windows OS are on separate partition, (or the Ubuntu directory has been moved to a separate ntfs partition), one can safely remove the partition containing the Windows OS.

3)  There is nothing mysterious about my claims.   All I'm saying  is that Grub 2 is able to boot Wubi and that Wubi does not depend on the Windows operating system.  

4) In a case like this, where all the data is backed up and Wubi was only run for a couple of days, I strongly recommend  to get rid of Wubi and do  a fresh install. 

> The problem is that windows has some unmovable files and i can not make a partition any bigger then 10gb without my windows going corrupt!


Since you are planing to delete Windows in a couple of weeks, why don't you just wait. Once you are ready to delete Windows, install Ubuntu with the "use entire hard disk" method.

> Edit: I just read i can keep my wubi okay so can i just extend the partition after deleting windows? 
Although it should be possible, I don't know how to extend the  Wubi partition without Windows. 

> if wubi will work i have no problem with keeping it as long as there are no disadvantages
Everybody in this thread seems to agree on one thing: a regular install is better. I have seen cases where  Wubi  has vanished  after an unclean shutdown.

---

