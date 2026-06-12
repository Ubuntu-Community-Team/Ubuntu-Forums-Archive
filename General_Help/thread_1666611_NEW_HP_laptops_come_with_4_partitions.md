---
title: "NEW HP laptops come with 4 partitions???"
date: 2011-01-13
forum: General Help
---

### Post by uberlube on 2011-01-13
hey guys, i just bought an hp g42 laptop and was distressed to go home and find out whilst trying to dualboot that hp ships with 4 partitions in use........I MEAN WTH!!!! why on earth would any manufacturer use up all 4 primary on nonesense? anyways rage aside, does anyone know the best way to rectify this without sacrificing HP_TOOLS and RECOVERY? the first partition is called BOOT and is quite small but im sure that if i just delete it everything will cease to work. Is it possible to clone one of them using clonezilla, then delete it, and in its place create the extended container and then drop it back in as an extended? Pls only give advice if your are sure it will work as I dont have recovery CD's (im a tech and bought this computer on clearance at work, the origional owner never returned the recovery CDs we made so making more wont work).

thnx guys :D

---

### Post by srs5694 on 2011-01-13
One of those partitions has the equivalent of a recovery DVD set on it. There's a Windows utility to create the recovery DVDs that HP was too cheap and inconsiderate to provide with your computer. Run it. Run it again. (Burned DVDs aren't as reliable as pressed DVDs.) While you're doing this, write a letter to HP (with a cc: to Microsoft) telling them how cheap they are; they'll keep pulling this crud if people accept it. Once you've made the backup discs, you can delete the partition in question. (It's about 15 or 20 GB, IIRC.)

---

### Post by Bitrate on 2011-01-13
Why don't you just make a recovery CD to start with so you have it when you need it ?

After you do that, backup all the non-system partitions to CD/DVD/USB hard drive and then run Gparted to create the partitions you want for your Ubuntu installation.

It looks like the BOOT/HP_TOOLS partitions might be linked to your systems BIOS - you will have to check.

---

### Post by Jerry N on 2011-01-13
I haven't tried it yet on my HP Mini 210 but one of those partitions contains some HP utilities could probably be eliminated.  The order on my Mini is System-199MB, NTFS-218GB,Recovery-14GB, HP Tools-103MB.  It is my opinion that the HP Tools partition could be deleted using gparted and the NTFS partition shrunk using the Win 7 tools.  This would create a place to put an extended partition that could then be used for the necessary logical partitions for Ubuntu.  

If you try this, please post your results.

Jerry

---

### Post by Jerry N on 2011-01-14
> **srs5694 said:**
> ...There's a Windows utility to create the recovery DVDs that HP was too cheap and inconsiderate to provide with your computer. 

Is it because HP (and all the rest of them) is too cheap or is it because we all expect to get our hardware at the lowest possible price?  And will the typical user even know where those disks are when it comes time to redo the system?

Since hard drives are big, including a restoration partition is no big deal but HP could put their tools in a file and there is no reason for that little boot partition.  That thing is not there when I install Win 7 from scratch!

Of course not one laptop user in 100 will even know that all 4 partitions are used up, or even know or care what a partition is.

Jerry

---

### Post by Quackers on 2011-01-14
Oh they'll know about it if they create a 5th partition!
I smell the Microsoft smell in this 4 primary partitions business! Very fishy :wink:
I believe that the HP TOOLS can be downloaded separately - check first! It's diagnostic stuff that, hopefully, nobody will ever need - computers being so good these days! :-) 
Other users have deleted that partition and installed Ubuntu that way.
I agree with srs5694 - write to HP telling them what you think.
I honestly wouldn't buy one for this reason alone!

---

### Post by srs5694 on 2011-01-14
> **Jerry N said:**
> Is it because HP (and all the rest of them) is too cheap or is it because we all expect to get our hardware at the lowest possible price?

That's a convenient excuse for the manufacturers, but I don't buy it. Providing users with a real DVD (or even several real DVDs) would add such a tiny amount to the price of the computer that it wouldn't make any difference to the average consumer's purchase decision. (I find it hard to believe that pressed DVDs cost more than a dollar or so, given that cut-rate DVD movies sell for $5 or less.)

> Since hard drives are big, including a restoration partition is no big deal

The problem is that one major reason for system re-installation is that hard drives can and do fail. Even without physical failure, the drive's contents can be damaged by bugs or user error. If you lack separate physical media, a failed or overwritten hard disk means you must go out and buy something -- either a new store-bought version of Windows (and *not* the upgrade version, since you won't have media it can verify) or a DVD set from the computer manufacturer (which will be cheaper, but the computer manufacturer willl sell it for much more than it's worth, since they've got a monopoly on the restore media).

Call me cynical, but this smells like a way for the computer manufacturers to get an extra couple bucks profit on new sales and then milk customers out of more money down the road when they need to buy installation DVDs because of failed hard disks. Quackers' suggestion that Microsoft might be pushing such configurations also makes sense. The 4-partition layout discourages multi-booting and the lack of physical media encourages people to upgrade if they need to re-install after the next version comes out.

---

### Post by srs5694 on 2011-01-14
More unwanted multi-posts....

---

### Post by Skrapp_Jaw on 2011-01-19
My experience with a G42-410US x64 Intel Chipset

I have been tooling with Ubuntu 10.10 Maverick on an HP dv2500 and it has been a learning experience. The laptop dual boots with XPpro x64 and runs really well. So, a friend of mind came to me with his HP G42-410US, trusting my experience with an HP in x64 arc, and the drives looked just as you described. Nothing went as expected. Here was the list of events I attempted...

Using win7 partition utility, I shortened C:\ drive by 80gb.

Ubuntu 10.10 x64 did not see the unused partition space as usable during the install.

Reboot win7 and format unpartitioned space to NTFS.

Reboot Ubuntu 10.10 x64 live install. I then reformatted that new NTFS into the linux ext format, and selected GRUB to go to the MBR.

Reboot after Ubuntu installation and ended up in the terminal with no GUI ubuntu desktop. The tty1 login and command lines were available but I have a very limited knowledge of terminal use. Enough to browse file folders and follow instructions.

So I rebooted and saw the grub boot loader. I then selected Windows 7 on sda2 and it seemed to be loading. After a brief view of the Windows 7 animation at startup it flashed to a black screen telling me that windows failed to boot and run the System Recovery Disc.

Unfortunately... This is where it got in trouble. The recovery disc could not read the partitions, or detect the windows 7 OS on the hard drive or the partitions. For lack of a better phrase, Epic Fail.

From here I loaded puppy linux on my flash disk.

In Gparted all partitions were visible, EXCEPT the original BOOT partition was a black box with a yellow triangle.

So, we decided to just give HP and win7 the finger and just wipe it clean. XP x64 and Ubuntu 10.10.

Long story short: Don't mess with those drives if you care about your warranty or that hard drive. Even after a clean wipe and install, all attempts to install XP failed due to a blue screen of death even before the setup disc began. Ubuntu installed but could not load the Desktop GUI at all. Command line terminal only. Also after about a minute of being idle, Ubuntu would drop into a sleep mode until the power button was pressed and then would shut down or restart the system.

Seems like however HP installed it's win7 distro is done to discourage dual booting. I have fought this all day and done nothing but lose ground. I'm gonna try to use a brand new HDD and see if anything different happens.

Also, all install CD's were used to install Ubuntu and XPpro x64 on the other HP laptop.

All Live media OS's boot fine from CD or USB.

---

### Post by coldraven on 2011-01-20
If you get the dual boot working don't ever select the "HP Restore" boot option.
Even if you do nothing and select "Cancel" it will already have overwritten your GRUB.
Because of all the bloatware (Roxio etc.) I wiped my hard drive and stuck Windows where it belongs, in a VM!

---

### Post by Skrapp_Jaw on 2011-01-24
Update. If you install Ubuntu and get the terminal tty1 login, just restart the laptop and hold shift for the grub menu or if you have windows in there still, just select the recovery mode and then use the low graphics mode. you can update from there to the newest kernel and then the gdm will load fine after that.

---

### Post by pharbar on 2011-01-25
I'm just about to install Maverick on an HP Probook and am interested to see how others got on. Please post any stories of SUCCESSFUL Win7 / Ubuntu installations on new HP laptops.

@Skrapp_Jaw: You don't mention the question of the primary/extended partitions and seem to have tried to create a 5th primary partition in the space you freed up. Could you clarify please?

Others seem to have had success beating HP's 4 Primaries setup thus:

a) shrink the C: drive
b) make an image of HP_TOOLS, then delete the partition
c) move things so that the newly freed space is at the end of the drive
d) create an extended partition
e) create a logical partition (at the end of the drive) for HP_TOOLS, and restore the image there
f) install Linux in the free space at the beginning of the extended partition

If that works, could someone please confirm it?

Others have suggested that HP_RECOVERY is not essential once back up disks have been made. True or False? That would free another primary slot for a possible XP installation.

I have also heard that the SYSTEM partition (which I presume acts as some kind of boot loader) can into boot Win7 even if it is on a LOGICAL drive. Does anyone have information on this?

NB: These are questions - I don't know the answers - so PLEASE don't try any of this out unless you know what you are doing!


Finally - imaging software...
I once used Clonezilla and had doubts and then a major problem with the 'Save MBR' option. There is also Partimage. Which would be best for

a) imaging single partitions
&
b) imaging an entire hard drive (i.e. to back up the virgin drive BEFORE I start messing about so I can go back to Square 1 and not risk nmy warranty)?

Sorry for LONG post!

---

### Post by Skrapp_Jaw on 2011-01-30
@pharbar: The extended partitioning for swap_files I left to the installer for Ubuntu. Unfortunately I lost the battle with the 4 partitions and Win7 on that machine. Ended up wiping it clean and starting from scratch.

---

### Post by colinwhipple on 2011-05-22
I have an HP G42 series laptop.  After a couple of attempts that didn't work, I installed Ubuntu 10.10 on it as follows:

1)  In Windows Control Panel, I shrunk the C drive down to about 140G.

2)  I created the Recovery DVDs, and then deleted the Recovery Partition.

3)  Using EASEUS Partition Manager in Windows, I converted the hard drive from Dynamic to Basic.  (this is the step I don't see anyone else mentioning)

4)   Still using PM, I created several logical drives, implicitly in an extended partition, filling all the space between Drive C and the HP Tools partition.

5)  I then installed Ubuntu from a USB flash drive.

Both Windows and Ubuntu are now both booting fine.  Grub2 controls the boot process.

Colin

---

### Post by srs5694 on 2011-05-22
> **colinwhipple said:**
> 3)  Using EASEUS Partition Manager in Windows, I converted the hard drive from Dynamic to Basic.  (this is the step I don't see anyone else mentioning)

To the best of my knowledge, HP ships its disk using standard MBR ("basic") partitions, not Microsoft's proprietary "dynamic" partitions. It's easy to accidentally convert from basic to dynamic by using Microsoft's partitioning tools, though. Perhaps you did this when shrinking the C: partition. It's also possible that HP has changed its partitioning system to use dynamic disks by default, or shipped some computers like this in the past.

There are lots of threads on this topic, but they mostly crop up when people try to prepare a disk with 3 or 4 primary partitions for Linux by creating Linux partitions in Windows. This typically goes over the 4-primary-partition limit of MBR and Microsoft's tools convert the disk to "dynamic" format. Thread topics are likely to be something like "Linux and Windows disagree on partitions" or "Linux sees wrong number of partitions."

---

