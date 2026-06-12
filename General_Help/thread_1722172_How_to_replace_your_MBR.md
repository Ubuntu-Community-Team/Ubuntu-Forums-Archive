---
title: "How to replace your MBR?"
date: 2011-04-05
forum: General Help
---

### Post by piro_ko88 on 2011-04-05
Long story short (but written with detail in case its important)...
I was trying to install Windows XP to a friends HDD via USB cable.
The correct HDD was wiped, formatted and installed, however the disk then proceeded to replace my OWN HDD's MBR. It was apparently part of the process of installing XP because it said "please restart to finish installation" or some such. Only upon restarting there were issues because whatever automatic command was written to MY MBR to help Windows finish installing upon reboot, it isn't able to recognize USB HDD's.
SO
FORGET the HDD I was installing XP on, it's another story that I've already taken care of.

HOWEVER!
My HDD's MBR was altered in the process, making my Windows Vista and Ubuntu inaccessible.
I recognize that that means GRUB is gone or only half there.

HERE IS WHAT I NEED TO KNOW:

I am using an Ubuntu boot CD and using the "try it" option to write this post inside the CD environment.
I have run
```
sudo fdisk -l
``` and been told: "Disk /dev/sda doesn't contain a valid partition table"
Which is kind of expected given the lack of MBR.

Durring a previous attempt to fix this I used another tool to completely wipe the MBR off my HDD because it seemed the best way to replace it at the time.

I am assuming I need to use "apt get" (I think I spelled that right) to install GRUB to my HDD? If so how exactly do I go through this process and will this really fix the problem?

Thanks for reading.:)

---

### Post by wilee-nilee on 2011-04-05
Boot the Ubuntu live cd go to the desktop go to gparted and post a screen shot of it.

---

### Post by piro_ko88 on 2011-04-05
Like so?

---

### Post by dragonfly41 on 2011-04-05
Today I fixed MBR by reading this ..

[http://blogs.deepal.org/2009/06/how-to-fix-mbr-using-ubuntu-live-cd.html](http://blogs.deepal.org/2009/06/how-to-fix-mbr-using-ubuntu-live-cd.html)

> When we have dual boot there are some possibility that we might delete  one of the partition, and causing deleting MBR as well. Issues can be  easily fix using Windows CD, however you need to remember the password,  if not ..

Ubuntu Live CD comes handy this case, just follow the following steps, you will be back in business.
Boot from Ubuntu Live CD
Then you need to download the ms-sys, you can find that from - [http://packages.ubuntu.com/dapper/i386/ms-sys/download](http://packages.ubuntu.com/dapper/i386/ms-sys/download)
Once downloaded it will ask for auto install, click that
Next type “sudo fdisk -l” , from that you can find the main partition you want to fix
Then type “sudo ms-sys -m /dev/sda”
Next restart, everything should work fine.

---

### Post by piro_ko88 on 2011-04-05
> **dragonfly41 said:**
> Today I fixed MBR by reading this ..

[http://blogs.deepal.org/2009/06/how-to-fix-mbr-using-ubuntu-live-cd.html](http://blogs.deepal.org/2009/06/how-to-fix-mbr-using-ubuntu-live-cd.html)

Dunno if I like the sound of that, but I'll try it if there's no other suggestions. : /
I need to replace my MBR entirely, not repair it, so it may be more tricky.

---

### Post by wilee-nilee on 2011-04-05
> **piro_ko88 said:**
> Like so?

I have never seen ms-sys advised in this circumstance and in hardly any others it is outdated, I believe. **dapper** main universe,  

So I would wait for some help from a more sure response. Chances are you will have to start with testdisk but I am not sure.

---

### Post by piro_ko88 on 2011-04-05
> I have never seen ms-sys advised in this circumstance and in hardly any others it is outdated, I believe. **dapper** main universe,  

So I would wait for some help from a more sure response. Chances are you will have to start with testdisk but I am not sure.

Thanks for the input, I'd rather avoid anything sketchy seeing as this has a potential of making a perfectly recoverable drive into a very long, complicated procedure that involves reinstalling OSs and needing to salvage (and probably leave behind by accident) important files.

---

### Post by Stephen Morgan on 2011-04-05
You might want to read up on testdisk while you're waiting for a response, you'll probably need to use it to put your partition table back together. The GRUB part of the MBR can be reinstalled from the live CD with the grub-install command, not with apt-get. I believe you mount your ubuntu partition, chroot into it, run grub-install on that partition, but you can't do that without a working partition table first.

For future reference, it's possible to back up your MBR, with the command:

```
dd if=/dev/sda of=backup.mbr bs=512 count=1
```


Not that any of that will help you now, though.

---

### Post by dragonfly41 on 2011-04-05
I hesitate in offering another sketchy idea .. but I've been wandering in the "failed windows" forest and after a while you try out anything .. provided you've backed up your files.

I found Parted Magic to be extremely useful.   Burn to bootable CD.

[http://partedmagic.com/doku.php](http://partedmagic.com/doku.php)

testdisk is one of the many tools in this CD.

---

### Post by oldfred on 2011-04-05
MBR has two important parts. The boot code for whatever system you are booting - windows, grub, grub2, lilo, syslinux etc. And it has your partition table.

If you overwrote both parts you cannot just reinstall the boot loader and have it work, but have to restore the partition table. If you do not have a backup (most of us do not), testdisk may be the best choice to try to recover it. Did you ever run boot info script or other tools that may have printed out partition table? That could be used to manually rebuilt table.
repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)


If testdisk restores partition table then you can reinstall your boot loader.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by piro_ko88 on 2011-04-05
> **oldfred said:**
> MBR has two important parts. The boot code for whatever system you are booting - windows, grub, grub2, lilo, syslinux etc. And it has your partition table.

If you overwrote both parts you cannot just reinstall the boot loader and have it work, but have to restore the partition table. If you do not have a backup (most of us do not), testdisk may be the best choice to try to recover it. Did you ever run boot info script or other tools that may have printed out partition table? That could be used to manually rebuilt table.
repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)


If testdisk restores partition table then you can reinstall your boot loader.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

AWESOME, thank you.
I never printed out a partition table.
I shall try those first few links and attempt to recover my partition table. Thanks very much to everyone who has helped so far. Greatly appreciated.
I'll post back once I attempt the partition table recovery.

---

### Post by piro_ko88 on 2011-04-05
I first used the detailed instructions on [http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/) to install testdisk. After the install I referred to [http://members.iinet.net.au/~herman546/p21.html#Recovering_a_Lost_Partition_With_](http://members.iinet.net.au/~herman546/p21.html#Recovering_a_Lost_Partition_With_) 
After proceeding to make sure I opened it with the terminal, I put in ```
sudo testdisk
``` and proceeded to follow the instructions given by the last link mentioned.
This has apparently recovered my partition table.

---

### Post by piro_ko88 on 2011-04-05
I have seemingly downloaded GRUB successfully.
Should I also download the Vista bootloader as well since I am trying to dual boot?

---

### Post by oldfred on 2011-04-05
There is only one MBR (Master Boot Record) per drive, the first sector on the drive.

You only install one boot loader to the MBR. Windows will only boot windows. Grub2 will find your windows install (if it is working) and let you boot it.

If not auto found, run this from the terminal.

sudo update-grub

---

### Post by piro_ko88 on 2011-04-05
Intended purpose complete.
MBR is fixed/replaced.
Upon boot everything is back to normal.
Or it would be...

Turns out part of my ORIGINAL problem of getting Vista to run isn't the MBR. I'm almost positive however that running my recovery disk I got with the laptop should fix the problem as all my Vista files were viewable when the HDD was plugged into another computer. 

I'll mark this as solved but post again later to say if the repair CD fixed the issue with Vista booting. If not it should probably be a new thread.

---

### Post by JKyleOKC on 2011-04-05
Be very cautious about using that Windows recovery disk, if you have any files in Windows that you want to keep. Many so-called recovery disks actually wipe the whole drive back to factory condition, losing all of your private files. To be safe, use the Ubuntu partition to copy all of your important files out of Windows onto an external drive!

If your recovery disk is like many of them, it will also destroy your Ubuntu installation in the process of "restoring" the entire drive, not just the Windows partition. Thus it's best to copy anything important to an external drive before running it.

This warning may not be necessary, but it's better to have a backup and not need it, than the other way around!

---

### Post by piro_ko88 on 2011-04-05
I'm unsure of whether to post this in a new thread...
Ubuntu boots fine, and works just like before.
From within Ubuntu my Vista is viewable and I can grab files as I please (so copying them can be done) however when I choose to boot Vista from Grub it starts by showing me an option between two types of Windows XP to choose Home or premium, or something of that nature before telling me there are problems with the install.

So here's the things. This is the same problem as I had before, only before I had no GRUB, and no access to Ubuntu. Now I do, but my Vista is still inaccessible because of something that happens somewhere between selecting Vista in GRUB and starting of Vista.

There's some files left in there from when I tried to install XP to an external HDD that seem to be causing the problem. My repair disk supposedly repaired the Vista that it found, and said it should be running fine. (I didn't choose to reset to factory default or wipe the disk, just repair existing Windows installations)
However it clearly is not.
Is this perhaps because the file that GRUB is using to start Vista is actually not vista at all but XP, and that some other file is needed to start my perfectly good (or seemingly good) Vista partition?

At recommendation I will move this to a new thread...

---

### Post by wilee-nilee on 2011-04-05
Lets see the bootscript now it is in my signature just click it and run it, and post all the text from the generated file in code tags. This will show more info about the vista and xp conundrum.

Good job on using testdisk, I was hoping oldfred would stop by with some help, he has the killer links and the knowledge as well.:)

Start a new thread though if you want.

---

### Post by piro_ko88 on 2011-04-05
This will be taken care of in a new thread as the original issue posted was (for the most part) solved.
Thanks for the help.

---

