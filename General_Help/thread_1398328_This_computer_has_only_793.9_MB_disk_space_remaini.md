---
title: "This computer has only 793.9 MB disk space remaining"
date: 2010-02-04
forum: General Help
---

### Post by Jonners59 on 2010-02-04
My Lpatop has a 300G hard drive.  It came, as many do pre-installed with a Window OS, in this case Vista 32-bit Home Prem.  I had partitioned the hard drive to give a C drive of 97.7GB (Partition 2 /dev/sda 2/Host), a partition for applications and programs, D of 48.8GB (Partition 3 /dev/sda3) and a third partition, E for Documents, etc. of 148GB (Partition 5 /dev/sda 5  media/doc), which on scanning seems to be a sub set of a partition Partition 4 W95 Ext d LBA   dev/sda 4.......

There is another partition, Partition 1 /dev/sda1 and is called WinRE and is of 2.80GB.

All are NTFS except for the Partition 4

Windows works fine and I have no problems, but when I use Ubuntu I get errors on startup.  In the first instance it will not install the latest Kernal and it gives a Battery Management error in GNOME.  I get Storage warning messages all the time, which I believe is the cause of the problems.  See enclosed.

I am assuming that the disk space issue is in Host and or Home.  Other than all the operational data and applications I do NOT use the Ubuntu filing system, rather the Partition 5 which I created solely for this purpose, so it's not a case of deleting files, it is purely how Ubuntu created itself on install and its operational requirements.

The problem is resulting in no space or ability to do updates and new installs, and Kernal and Gnome issues.

Can anyone help me, please?

I have tried other threads to get this fixed to no avail.

---

### Post by oldos2er on 2010-02-04
Can you run **sudo fdisk -l** in a terminal, and post the output here? Did you use Wubi to install Ubuntu?

---

### Post by Jonners59 on 2010-02-04
> **oldos2er said:**
> Can you run **sudo fdisk -l** in a terminal, and post the output here? Did you use Wubi to install Ubuntu?

Thank you.

Please see screen-shot enclosed with results

If that is the Windows download version rather than disc, etc, then yes.

What's the diagnosis Doc?

---

### Post by oldos2er on 2010-02-04
You'll need to increase the size of root.disk. Whether you can do this from within Windows or if it requires a reinstall of Wubi, I don't know; perhaps someone else could help you with that.

---

### Post by Jonners59 on 2010-02-04
> **oldos2er said:**
> You'll need to increase the size of root.disk. Whether you can do this from within Windows or if it requires a reinstall of Wubi, I don't know; perhaps someone else could help you with that.

Thank you.  Yes, I thought so too, but like you I have no idea as to how.  You mentioned doing via Windows.  Would you know how I would identify it (root disc) when viewed via Windows?  The folders seem to be labelled differently.  If I can identify then there is a great little app (Acronis) that works very well on Western Digital HD when working in Windows that can allow complete reconfigureation of HD......

---

### Post by sailthesea on 2010-02-04
When you install with Wubi you are given a choice of size for the OS and as far as I know you cannot change this later on
 There is a tip that may help though In the Ubuntu system files (accessed from inside Ubuntu) is a file called host This is actually windows you can move files into the Windows system and create some room or save them if you reinstall
As a rule important files should be kept there anyway if you use Wubi
Good luck!

---

### Post by oldfred on 2010-02-04
root.disk is just a file within the partition. How much of the partition is it using.


An aside. Your winRE partition is to let you write a recovery cd/DVD so if your system crashes you may be able to repair it. Anyone with a new windows system should do that first.

---

### Post by Jonners59 on 2010-02-04
> **sailthesea said:**
> When you install with Wubi you are given a choice of size for the OS and as far as I know you cannot change this later on
 There is a tip that may help though In the Ubuntu system files (accessed from inside Ubuntu) is a file called host This is actually windows you can move files into the Windows system and create some room or save them if you reinstall
As a rule important files should be kept there anyway if you use Wubi
Good luck!
That's where Ubuntu goes wrong, it assumes everyone is competent and informed with it.  It should explain this and make recommendations.

I do not keep files within Ubuntu or Windows for that matter.  They are all stored either on a remote server or in the partition especially created for that purpose, so IF I were to move anything it would be "bits of" Ubuntu.  Can I do this?  And if so which folders?

I am reluctant to rebuild Ubuntu as it took me ages to get it to this working state.

If I were to rebuild....  Which folders could I copy/move across into HOST to then re install after to make the system work as pre rebuild...  If that makes sense?

---

### Post by Jonners59 on 2010-02-04
> **oldfred said:**
> root.disk is just a file within the partition. How much of the partition is it using.


An aside. Your winRE partition is to let you write a recovery cd/DVD so if your system crashes you may be able to repair it. Anyone with a new windows system should do that first.

Oldfred,
Does the enclosed screen shot answer the question?  I am not sure which refers to the root. The total Hard Disk is 300G, so this is only a Partition within. Also note my first entry which has the Partitions created before I installed Ubuntu and how they are used.

Re WinRE.  I wondered where it came from and what it was for.  Perhaps you could point me in a direction to understand how to use it, please.  Sounds as if it would be a good idea!!!!

Many thanks:D

---

### Post by sailthesea on 2010-02-04
> **Jonners59 said:**
> That's where Ubuntu goes wrong, it assumes everyone is competent and informed with it.  It should explain this and make recommendations.

I do not keep files within Ubuntu or Windows for that matter.  They are all stored either on a remote server or in the partition especially created for that purpose, so IF I were to move anything it would be "bits of" Ubuntu.  Can I do this?  And if so which folders?

I am reluctant to rebuild Ubuntu as it took me ages to get it to this working state.

If I were to rebuild....  Which folders could I copy/move across into HOST to then re install after to make the system work as pre rebuild...  If that makes sense?


 You can't move "bits" of Buntu unfortunately
If you reinstall Wubi with a bigger virtual disk or try a dual boot this time you can reconfigure the system quite quickly by dumping a log file onto a USB stick and then using the terminal to restore the changes you have made

Check my thread from a while back:
[http://ubuntuforums.org/showthread.php?t=1240550](http://ubuntuforums.org/showthread.php?t=1240550)

 Bear in mind this was for Jaunty so you may need to modify the commands but the principle remains the same
 Hope this of some help

---

### Post by oldfred on 2010-02-04
I am not a big fan of wubi, have not used it. It is good for windows users who want to get acquainted with Ubuntu. It does not required repartitioning which often scares new users away. It works better than a liveCD so it does have some advantages.

If you are using Ubuntu a lot it is time to think about repartitioning and doing a full install. I used ubuntu for 3 years with just root (/) and swap with a small shared NTFS partition as we converted from windows to Ubuntu. With Karmic I did convert to separate /home and another partition for data as ext3.

You should be able to boot into the recovery partition and it will give you a choice to write CD. I did that 3 years ago for my portable but do not remember the details. I do not ever plan on using it now as I am almost totally converted to Ubuntu.

---

### Post by Jonners59 on 2010-02-04
There is a lot for me to grasp in these two messages, especially as I am not used to command line or Ubuntu.  I am going to have to read the links you have provided and see what they say.  I was wondering though.

Acronis works really well, so IF I can identify the actual Folder that is shy on storage I believe I could expand it.  It may be worth the gamble...

I'm going to pick this up from 15th as this is so complex and I have exams all next week....

I hope you will pick this up with me when I restart then.  Thank you for you help so far.

---

### Post by meierfra. on 2010-02-04
If you have enough free space on your Windows partition, you  should be able to resize your  Wubi file  with LVPM:

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

---

### Post by sailthesea on 2010-02-04
> **Jonners59 said:**
> There is a lot for me to grasp in these two messages, especially as I am not used to command line or Ubuntu.  I am going to have to read the links you have provided and see what they say.  I was wondering though.

Acronis works really well, so IF I can identify the actual Folder that is shy on storage I believe I could expand it.  It may be worth the gamble...

I'm going to pick this up from 15th as this is so complex and I have exams all next week....

I hope you will pick this up with me when I restart then.  Thank you for you help so far.

 No sweat
 Nothing has actually broken yet, maybe there is a way to resize the Wubi install Just don't run any updates or install anything else! 
 Good Luck with the Exams;)

---

### Post by Jonners59 on 2010-02-04
OK, another option.  Looks good.

I have loads of space on the partition. so I can move stuff about, but as I do not know what is what I am concerned I move the wrong thing or damage something.......  If I knew exactly wich folder/partition is at fault and needs "expanding" I can make a judgement...

---

### Post by sailthesea on 2010-02-04
> **meierfra. said:**
> If you have enough free space on your Windows partition, you  should be able to resize your  Wubi file  with LVPM:

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

Thats a nicer option than the CLI commands

Don't be hasty and take the time to understand what you are doing You will learn a lot more than you realise!

---

### Post by oldos2er on 2010-02-04
> **Jonners59 said:**
> That's where Ubuntu goes wrong, it assumes everyone is competent and informed with it.  It should explain this and make recommendations.

To my knowledge the psychic OS has not yet been invented. :)

Wubi's not really meant to be permanent; think of it as a demo. I see lvpm was already mentioned; you could tar or zip your current home directory, including hidden files, which would preserve some of your configuration.

---

### Post by Jonners59 on 2010-02-12
> **sailthesea said:**
> No sweat
 Nothing has actually broken yet, maybe there is a way to resize the Wubi install Just don't run any updates or install anything else! 
 Good Luck with the Exams;)

Hi I am back, and starting off again.

Status:
I tried removing some applications like WINE, this then allowed the Update application to start working again, and it automatically downloaded the latest images.

I then followed the advise to resize my  Wubi file  with LVPM.  I resized down the drive that I use for my files storage on.  Then used this to add to the "C" Drive which has my Vista and the Ubuntu on, not that the drive was full, but it made it very large for just OS!!!

Anyway from that point onwards Ubuntu will not load.  When I select Ubuntu it starts to load but before it gets to the list of images to choose from it flashes up an error and then the screen says:[B]
GNU GRUB Version 1.97~beta[/B]
*Some words about options, then*
**sh:grub>**

I have tried many times to restart and get it going but it makes no difference.

I then tried to follow the rest of the instructions to resize the Wubi...  LVPN says to change the partitions to ensure there are two new unused, one called SPARE.  However the LVPM Partition Manager would NOT allow me to create any more partitions (nor other tools I tried), says 4 is the max and I need 6 with the two new ones to allow the application to work...

Also, it would NOT allow me within the partitions to change any folders size (Wubi), not that I know which to change...

So, we have Windows working fine.
The origional problem of no space still exists, even though I still have about 250G free.
Then the images would not work because they could not load the Kernals for the newer images
And now Ubuntu will not start at all.

?Help?????????

---

### Post by oldfred on 2010-02-13
Some other threads with suggestions on solutions for wubi issues:
[http://ubuntuforums.org/showthread.php?t=1400608](http://ubuntuforums.org/showthread.php?t=1400608)
[http://ubuntuforums.org/showthread.php?t=1339203](http://ubuntuforums.org/showthread.php?t=1339203)

Your system has used all four primary partitions. You can only have 4 primary or 3 primary and one extended that is a container for logical partitions. Linux (and windows data) can be installed totally in logical partitions but windows has to be in a primary.
Reorganizing partitions when all four are used is a major task. You have to back up data and delete a partition, move/shrink other partitions to make space for a new extended and copy data back and add new partitions. If possible it is easier to add a hard drive.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

---

### Post by Jonners59 on 2010-02-14
Thanks for all this

> **oldfred said:**
> Some other threads with suggestions on solutions for wubi issues:
[http://ubuntuforums.org/showthread.php?t=1400608](http://ubuntuforums.org/showthread.php?t=1400608)
[]("http://ubuntuforums.org/showthread.php?t=1339203")

Tried this, but it did not work.  Made no difference.

> **oldfred said:**
> 
[http://ubuntuforums.org/showthread.php?t=1339203](http://ubuntuforums.org/showthread.php?t=1339203)

Your system has used all four primary partitions. You can only have 4 primary or 3 primary and one extended that is a container for logical partitions. Linux (and windows data) can be installed totally in logical partitions but windows has to be in a primary.
Reorganizing partitions when all four are used is a major task. You have to back up data and delete a partition, move/shrink other partitions to make space for a new extended and copy data back and add new partitions. If possible it is easier to add a hard drive.

Tried the above, which also did not work.  That said the Partition Commander is excellent and deffinatly is the best I have come across.  I have, however managed to create all the partitions required.

I now have:

C - Vista and origional Wubi (which I guess I need to move)
D - Applications and Programs for my Windows OS
Then in an Extension I have the following:
E - Documents (for both systems)
F - empty formatted as Linux Share
G - WinRE which I created by copying the origional
L - emplty formated as Linux Ext 2

I now need to get my Ubuntu working again.  In esenece I still have the same problems.

The origional will be no spare memeory ( see below) whic was superceeded by
Not being able to load the new images as it could not find the Kernal, which was superceeded by the newer problem of failing all together
error and then the screen says:[B]
GNU GRUB Version 1.97~beta[/B]
*Some words about options, then*
**sh:grub>**


I would like to load the Ubuntu on the new empty Linux drive, known as L but I do not want to recreate everything as it takes for ever.  Is there a way of doing this by copying over folders or whatever.....  I basically now have a laptop that works fine in Windows Vista but my Ubuntu does not work at all.

---

### Post by oldfred on 2010-02-14
If you have created a linux root and swap partitions LVPM may work. I am not sure it works with the newest versions. You can install Ubuntu and copy /home over as it has most of your settings in hidden files(make sure you copy them also).

What else is it you are concerned about missing with a new install?

meierfra. has posted a page on repairs of wubi.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by Jonners59 on 2010-02-14
> **oldfred said:**
> If you have created a linux root and swap partitions LVPM may work. I am not sure it works with the newest versions. You can install Ubuntu and copy /home over as it has most of your settings in hidden files(make sure you copy them also).

What else is it you are concerned about missing with a new install?

meierfra. has posted a page on repairs of wubi.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

No, it just does not want to work for me....  I can not get Ubuntu to start I still get the same messages.

I think I will need to uninstall the current Ubuntu and install from the disc - yes, I have a disk copy...

As I can't get into Ubuntu, how do I find the Home folder and copy its contents to a safe location?

Re the question, what else....?  I would like to be able to keep all programes, settings, etc without having to rebuild.  But MOSTLY I am concerned because I set up my eMail in a client (can't recall it's name) with my calendar...  I don't want to loose the calendar.

---

### Post by oldfred on 2010-02-15
You can mount your wubi from another Ubuntu. This is a script to automate the process or you can type in all the commands. See discussion in thread for more info.
[Script] Mount Wubi Disk from Linux 
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)

Your /home should have all the info you want to copy. If you have space I would install Ubuntu and create the script to mount wubi from the new install. You could put the script on a USB key and copy it to your liveCD to run it also. Not sure if all the permissions will be ok.

---

### Post by Jonners59 on 2010-02-17
I did not get this far.  I ended up reinstalling Ubuntu from CD.

I needed to find the Home folder whilst in Windows as I had no access to Ubuntu.  I tried backing up the whole of my Windows C Drive, but that failed.

I used the really good Partition Commander ap to shuffle my partitions round, creating 2 Linux 3Etn within the Extenstion partition - I had already used up all of my primary slots.

I then installed the Ubuntu, which cleared out almost all the previous install - I say almost as I get additional OS selections at start up.

So, naturally, I lost all my settings so have had to rebuild everything from scratch.  It is a shame I could not find the Home folder from within Windows, I may have been able to "ring fence" it.

This has not really been a solution, but I have learned a lot about some of the Ubuntu limitations.[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

I still have some issues to resolve on this machine, and another I have just started updating from Windows to Ubuntu...  New threads.
[IMG]http://ubuntuforums.org/images/icons/icon11.gif[/IMG]
Thanks guys for all your help.  You have been great.

oldfred and sailthesea especially!

---

