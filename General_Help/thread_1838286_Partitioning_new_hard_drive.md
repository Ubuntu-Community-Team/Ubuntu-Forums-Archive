---
title: "Partitioning new hard drive"
date: 2011-09-03
forum: General Help
---

### Post by bradlees on 2011-09-03
On a new hp laptop I am attempting to dual boot ubuntu alongside of Windows 7. The install cd and usb do not give me a guided option to install ubuntu alongside windows as it says in many of the walkthroughs. I am a little leery of partitioning my hard drive without some advice. The drive is already in 4 partitions, 2 for windows and then 2 other ones which are HP recovery tools. Any advice on how to proceed?

---

### Post by LowSky on 2011-09-03
What version are you trying to install?

More than likely you are going to have to shrink the main windows partition, create an extended partition, then create a / (known as root) (as big as you wish, min I would suggest is 20GB, 30 would be better) and and swap partition (at least the size of your RAM).

---

### Post by coffeecat on 2011-09-03
> **LowSky said:**
> 
More than likely you are going to have to shrink the main windows partition, create an extended partition, then create a / (known as root) (as big as you wish,

Unfortunately, HP set up their machines with four primary partitions and you can't create an extended before you delete one of the primaries, and the big question is: which primary?

@bradlees, if your HP is like my HP and every one that I have seen posted about, your partition layout will be as follows:

Partition 1 - SYSTEM (your Windows 7 boot partition).
Partition 2 - Your Windows C: partition.
Partition 3 - The recovery partition.
Partition 4 - HP_TOOLS - a tiny partition right up at the top end of the drive.

I deleted my HP_TOOLS partition in order to be able to create an extended partition. More here:

[http://ubuntuforums.org/showpost.php?p=11025958&postcount=11](http://ubuntuforums.org/showpost.php?p=11025958&postcount=11)

There are some details in that post which are not relevant to you, but I think you will get the picture. Some people prefer to delete the recovery partition, but whatever you do create a set of restore DVDs before you delete anything.

Having done that, you will need the "something else" option in the Ubuntu installer and for that you need to know something about partitions. You will find this useful:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Take your time. Read it through + all the links. Then you will be well prepared to re-partition your HP machine. If you need any help, just post back! :)

**EDIT**: by the way, in my step 4, use the Windows Disk Management utility for shrinking the Windows partition. This is safer than using Gparted in Ubuntu. Then in step 5 use Gparted in the live Ubuntu CD to create the extended partition and the logical partitions you need for Ubuntu.

---

### Post by bradlees on 2011-09-03
That is how my hard drive is partitioned. I will read through those posts and hopefully proceed from there. I am a little uncertain about the extended partition though. 

THanks

---

### Post by coffeecat on 2011-09-03
> **bradlees said:**
>  I am a little uncertain about the extended partition though. 

An extended partition is merely a special type of primary partition that you don't use directly. Instead, it acts as a container for as many logical partitions as you may need. Linux can boot from a logical partition, unlike Windows which needs a primary partition to boot from. But the link I posted will tell you more.

Good reading and good luck! :)

---

### Post by oldfred on 2011-09-03
Lots of good info from coffeecat. 

I will add just one thing - repairCD. Recovery DVDs are just an image of hard drive as purchased and generally cannot be used for repairs.

Many users have no windows repairCD. With Ubuntu your install CD is a liveCD that you can use for repairs. And you can repair some but not all Windows things from Ubuntu. So make a Windows repairCD. We used to link to a site that would let you down load a repair Cd but now they want $10.

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by bradlees on 2011-09-04
Thanks coffeecate. Pointed me in the right direction. The only thing I got hung up on, and its probably my fault, was that I didn't realize I would have to use gparted on the live usb to create an extended partition, that I couldn't do that through the installer. Once I figured that out, problem solved. Thanks again.

I know this is slightly off topic, but I'm having  difficulty adjusting to the new touchpad on this hp as opposed to my previous laptop using windows 7. Things seem to be even worse on ubuntu. Issues checking off boxes and closing windows with a left click are prevalent. An hp thing, a driver or something?

Cheers

---

### Post by thilina on 2011-09-04
Remember to make a swap partition and give it a size of RAM*2

---

### Post by coffeecat on 2011-09-04
> **bradlees said:**
> 
I know this is slightly off topic, but I'm having  difficulty adjusting to the new touchpad on this hp as opposed to my previous laptop using windows 7. Things seem to be even worse on ubuntu. Issues checking off boxes and closing windows with a left click are prevalent. An hp thing, a driver or something?

On my HP netbook, the touchpad behaves very much the same in Ubuntu as in Windows 7. But it may be that the hardware used in your HP laptop is different from that in my netbook. All I can suggest is to see if adjusting the mouse settings helps. I'll assume you are using Ubuntu 11.04 with the Unity desktop. To get to mouse settings, click on the shutdown button top right (yes, weird! :)). Select System Settings -> Hardware -> Mouse. See if any of those settings help.

If you are using an earlier release of Ubuntu with the classic gnome desktop, you'll find mouse settings under System > Preferences.

---

