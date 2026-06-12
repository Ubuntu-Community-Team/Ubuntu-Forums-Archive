---
title: "Ubuntu does not find other Partitions"
date: 2010-03-12
forum: General Help
---

### Post by Gn0xter on 2010-03-12
Hey guys.
I just brought a netbook with win7 starter on it. Now it is formatted like this:
220gb win7
12gb recovery
199mb "System"
104mb "HP Tools"
 
I made a Life USB cause it has no Disk Tray.
Everytime I tried to install Ubuntu or UNR or XUbuntu or KUbuntu or whatever it only detected the USB and an empty HDD of 250 GB.
I tired everything. Gparted found the same. UNR showed me first 2 Partitions in menu but not more.
I tried to reinstall the life USB, defrag, wubi (wich always gave me an error like "no root data system selected" and now im finished with my ideas.
Can anybody help me?
I have no Idea what to do now.
 
Thanks a lot.

---

### Post by Mark Phelps on 2010-03-12
Without more info, I'm presuming that the four partitions shown are all Primary -- meaning, no installer is going to let you create another partition.

Creating Ubuntu partitions is going to be MAJOR work because you'll have to REMOVE one of the partitions you have already, shrink the Win7 partition (using the Win7 Disk Management utility), and then create a new Extended partition to hold the Ubuntu partitions.

What makes this a really risky operation is that you most probably have no ability to boot from a CD or DVD to do any restoration -- should something go wrong.

A fairly common problem is the inability to reboot into Win7 after such activities -- easily solved if you made a Win7 Repair CD (which, apparently, practically no one does!), and if you can boot from that CD to run some repairs.  But if you have no wait to do such a boot, you have no way to run repairs.

To add insult to injury, if you remove your Recovery partition, unless you are able to transfer this to DVD, you have no way of restoring your Win7 install should something go terribly wrong.

You could create a folder in your Win7 partition and migrate the contents of HP Tools there.  That way, you would still have them available.

Does your system provide the ability to boot from an external drive? If so, can it be USB or DVD?

I'm asking because, if you're interested in retaining what you have now in the Netbook, the first thing you should consider is backing up the entire drive to an external drive -- so that you can recover it later.

If you can do that, you're free to experiment at will with other options.

I just don't want to recommend anything that has the risk of rendering your netbook unusable.

---

### Post by Gn0xter on 2010-03-12
The major problem is this one:
Fdisk finds all partitions.
I just tried to Create a new volume with Win7 But it says, that the System is not Supporting this or something like that. I have created free Space now, but it does not work either.
Now looking up if fdisk finds the free space.
Would it be possible, to format the free space with fdisk and then to install Ubuntu there? Maybe I could create Ubuntu and GRUB 2 from there to Add windows 7 starter to Grub afterwards.

---

### Post by audiomick on 2010-03-12
> **Mark Phelps said:**
> Without more info, [COLOR=Red]I'm presuming that the four partitions shown are all Primary[/COLOR] -- meaning, no installer is going to let you create another partition..
This is likely to be your problem. You can only have four primary partitions on a drive (any drive, any OS), so if you already have four primaries, you wont be able to create any new ones even if you make empty space.

The advice that Mark Phelps gave you is good. I would also suggest doing some reading here
[https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Gn0xter on 2010-03-12
Windows shows me only 3 in explorer. System, Recovery and C:\.
Can I integrate one into another?
Or the one with HP Tools just format? I need Ubuntu. so what to do now?
HP Tools is not shown in Explorer. So how do I integrate it?

---

### Post by srs5694 on 2010-03-12
There are tools that can convert a primary partition into a logical partition, but I'm not familiar with most of them. The one I know most about isn't really designed for this purpose; it's my GPT fdisk program, which is primarily a tool for editing GUID Partition Tables (GPTs) rather than older MBR partition tables that this computer almost certainly uses. The latest GPT fdisk (0.6.5) does have a feature to convert from GPT to MBR, though, including support for logical partitions. Depending on where free space is located, it could convert some or all of the partitions from primary to logical form by way of GPT. This is roundabout and risky, but in theory it would work. I've done it in practice, but I can't promise it wouldn't trash your disk. I recommend looking for a tool that'll do it within the MBR framework. Then use that tool (if it supports partition resizing) or another one, such as GNU Parted, to resize one or more partitions to make room for Linux. (Linux will have to reside entirely in logical partitions, but that's fine.) Any conversion from primary to logical partition, by any utility, requires at least one free sector before each new logical partition, and those free sectors may not exist at the moment (except for the first partition), so you'll probably have to resize at least one partition just to do the conversion. Be cautious about resizing your main Windows partition; Windows tends to react badly to having its boot partition resized, especially if the start sector changes.

---

