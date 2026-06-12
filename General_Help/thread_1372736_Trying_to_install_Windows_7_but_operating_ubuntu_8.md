---
title: "Trying to install Windows 7 but operating ubuntu 8.04"
date: 2010-01-04
forum: General Help
---

### Post by WeMade on 2010-01-04
Hi ,  I've never posted on a forum but have always found them to be useful because someone else always had the same problem before me, and some where, there is someone who knows the answer.

I have been struggling to figure out ubuntu, I'm very new to Linux. I installed ubuntu onto my entire 500GB hard drive when my Vista crashed, it saved me I backed up all my files before I formatted to unbuntu by running the install cd. I just bought a copy of Windows 7 and tried to install it by booting the cdrom. When I got to the partitions in Windows install it said I had one dynamic like 460ishGB and a second 40GB partition. My drives weren't listed and Windows 7 said it was not able to install on hard disk space that isn't formatted as NTFS, and that the partition (480GB) was of unrecognized type. 

I've looked all over and feel like I may be missing something obvious because I can't seem to find a similar problem. Please help, I'd appreciate it !!

---

### Post by switch10 on 2010-01-04
> **WeMade said:**
> Hi ,  I've never posted on a forum but have always found them to be useful because someone else always had the same problem before me, and some where, there is someone who knows the answer.

I have been struggling to figure out ubuntu, I'm very new to Linux. I installed ubuntu onto my entire 500GB hard drive when my Vista crashed, it saved me I backed up all my files before I formatted to unbuntu by running the install cd. I just bought a copy of Windows 7 and tried to install it by booting the cdrom. When I got to the partitions in Windows install it said I had one dynamic like 460ishGB and a second 40GB partition. My drives weren't listed and Windows 7 said it was not able to install on hard disk space that isn't formatted as NTFS, and that the partition (480GB) was of unrecognized type. 

I've looked all over and feel like I may be missing something obvious because I can't seem to find a similar problem. Please help, I'd appreciate it !!

put in an Ubuntu live CD and run gparted.  reformat the drive (or a partition if you are dual booting) to NTFS.  Windows 7 will see it.

---

### Post by jamesisin on 2010-01-04
It sounds like you have one 500 GB drive in your machine?

You have likely installed Ubuntu so as to use that entire drive (somewhere around 450 GB of space).  This leaves you with no available partition to install another operating system.  Not even one so fancy as Windows 7.

You have a couple of options, three that come quickly to mind.

1. Run Windows 7 as a virtual machine on your current Ubuntu system
2. Add a second hard drive and install Windows 7 onto that new drive
3. Re-partition your current drive and install Windows 7 onto a new partition on your re-allocated current drive

---

### Post by WeMade on 2010-01-04
Thanks for replying!! 

When I was running vista I had a drive C and D each 250GB. Does that mean that I have to free up some space on a partition before I can reformat it to NTFS? Or can I run gparted and reformat without running Windows 7 as a virtual machine in ubuntu?

When I reran the ubuntu disk from boot I didn't see any gparted options, how do I get to it if thats a solution to the reformatting?

---

### Post by Sef on 2010-01-04
> 1. Run Windows 7 as a virtual machine on your current Ubuntu system

That may not be possible.  It would depend on the OP's CPU.

---

### Post by WeMade on 2010-01-04
I don't think I need to partition though, I forgot to mention that I would like to install and run only Windows 7 on my pc. So I guess I have to reformat my whole hard drive, the only other option in advanced options was to delete the 450GB partition.

---

### Post by wilee-nilee on 2010-01-04
> **WeMade said:**
> I don't think I need to partition though, I forgot to mention that I would like to install and run only Windows 7 on my pc. So I guess I have to reformat my whole hard drive, the only other option in advanced options was to delete the 450GB partition.

If you just want W7 boot the install DVD pick custom install and delete all the partitions and install.

---

### Post by jamesisin on 2010-01-04
If you are going to run a virtual machine, you can use VirtualBox.  It's by Sun and there is a free version.  Their site has a good how to for setting up a repository for their software (which means it gets added to Synaptic) and it's pretty easy to build a virtual machine once you get that added.

If you run a virtual machine you will not have to change any partitions.

However, if you choose to repartition (or if for some reason you are not able to run a virtual machine--lack of RAM or CPU power for instance), then you will have to repartition your drive.  This is dangerous so proceed with caution.

In order to change a partition the drive has to be in an unmounted state.  This means you cannot repartition your OS drive while booted into your system.  Instead you will have to download either a gparted live CD or an Ubuntu live CD (your installation CD is also a live CD if you still have it).

Boot into either gparted (or the installer in manual mode) and seek out options for moving a partition.

If you delete or over-write or otherwise destroy your OS partition you will be very sad.  You will want to shrink your OS partition toward the front of the drive.  Once you have shrunk it down (Windows should be fine with maybe 40 GB so shrink your partition down to say 400-410 GB).

Now you can boot back into Ubuntu.  From within Ubuntu you can then take that (now) unallocated space and create an NTFS partition for Windows.

Be very careful when you install Windows to only install on that newly created NTFS partition.

---

### Post by droadtrip on 2010-01-04
[FONT=Tahoma][SIZE=3][COLOR=DarkRed]I only read a couple responses and wanted to jump right in here and say something. Hopefully I'm not just giving the same advice. Get the application "GPARTED" from Add/Remove Programs or Synaptic. Then what I would do is a manual Re-partition of 50% to Windows and the other going to Ubuntu. I would only put about maybe 10 GB to Home, 2 GB to Swap, and 400(?) GB to Root, or "/". 

For the Windows side, I would just leave that whole space empty, since I already re-created the partition for Ubuntu. Save any important data in Ubuntu because it will be wiped during this process. Then Windows will see the empty partition and use that one. [/COLOR][/SIZE][/FONT]

---

### Post by WeMade on 2010-01-04
I don't know how to quote lol 

"If you delete or over-write or otherwise destroy your OS partition you will be very sad." 

I don't want to be more sad than I am! So deleting the partition would be really bad then I take it. 

So the partition I will be repositioning in gparted will be my ubuntu OS (the 450GB) but since I would be running the live cd then it would be okay? Then I can install windows on the smaller partition that has been NTFS formatted. In Windows 7, am I able to partition my whole hard drive to be windows if I wanted to?

---

### Post by droadtrip on 2010-01-04
[FONT=Tahoma][SIZE=3][COLOR=Navy]@WeMade. Yes, you could partition everything to Windows using the Live CD. I thought of this after my last post. GPARTED worked better when I had multiple distros, not just one distro. With the live CD, you could easily change the partitions to your desired size. 

I would say, yes to your last question in that you could have Windows take back over the Ubuntu Partition if necessary, but that is just in theory for me as I haven't tried it. I only take chunks from Windows for Linux and then re-divide within Linux only. That's just me. [/COLOR][/SIZE][/FONT]

---

### Post by jamesisin on 2010-01-04
Let's make sure we keep our language strait so you don't make any goofs based upon a quirk of language.

You have one hard drive.  That hard drive currently has one partition.  This current partition has Ubuntu already installed.

You would like to have two partitions on your one hard drive.  One partition will keep, intact, Ubuntu; and the other partition will receive a new installation of Windows 7.

In order to accomplish this you will want to boot into a live CD (either gparted or Ubuntu) and shrink single Ubuntu partition.  You will not need to do any other partitioning here.  You may reboot back into your installed Ubuntu to make certain all is well.

From within your installed Ubuntu, you may now use the unallocated space on your hard drive to create a second partition as an NTFS partition.  You may do this using Disk Utility (located under System --> Administration).

Make sure you understand all of this before proceeding.  Ask questions as necessary.

---

### Post by WeMade on 2010-01-04
I'm sorry! I haven't been so clear on everything.

I have 1 hard drive. When I installed ubuntu I choose for it to reformat my whole hard drive not knowing any better about partitions, but it automatically partitioned a small amount of the drive anyways, away from the 450GB (where ubuntu is installed). I only want Windows 7 to be installed with preferably no partitions but Windows can't recognize the big 480GB partition (I think the smaller partition that is there also needs to be formatted NTFS).

So I guess I need to format my 450GB partition and my like 50GB chunk to NTFS. 

Thank you for all of your advice so far!!! I won't do anything drastic until I'm sure I know I understand what could help.

---

### Post by k64 on 2010-01-04
> **WeMade said:**
> Hi ,  I've never posted on a forum but have always found them to be useful because someone else always had the same problem before me, and some where, there is someone who knows the answer.

I have been struggling to figure out ubuntu, I'm very new to Linux. I installed ubuntu onto my entire 500GB hard drive when my Vista crashed, it saved me I backed up all my files before I formatted to unbuntu by running the install cd. I just bought a copy of Windows 7 and tried to install it by booting the cdrom. When I got to the partitions in Windows install it said I had one dynamic like 460ishGB and a second 40GB partition. My drives weren't listed and Windows 7 said it was not able to install on hard disk space that isn't formatted as NTFS, and that the partition (480GB) was of unrecognized type. 

I've looked all over and feel like I may be missing something obvious because I can't seem to find a similar problem. Please help, I'd appreciate it !!

The problem is that if you have a partition formatted in EXT3 (the Linux default) you have to select "Drive Options (advanced)", select "Delete" and then select "New". You will then be able to install Windows 7 normally.

Linux partitions need to be deleted and reconfigured to work with Windows.

---

### Post by jamesisin on 2010-01-04
Please boot into your Ubuntu system and open a terminal.  Post the output of the following command into a code block:

df -h

[noparse]```
copy this and paste your output between these codes
```[/noparse]

---

### Post by WeMade on 2010-01-04
> **k64 said:**
> The problem is that if you have a partition formatted in EXT3 (the Linux default) you have to select "Drive Options (advanced)", select "Delete" and then select "New". You will then be able to install Windows 7 normally.

Linux partitions need to be deleted and reconfigured to work with Windows.


So it is safe then to delete the giant partition with ubuntu installed on it and make a new one? I'm not trying to save anything on my hard drive, I already have what I wanted to save backed up on an external hard drive so I have no problem reformatting or deleting as long as it doesn't render my hard drive useless ... and I can still install Windows 7.

---

### Post by WeMade on 2010-01-04
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             454G  2.9G  428G   1% /
varrun                1.5G  100K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   64K  1.5G   1% /dev
devshm                1.5G   12K  1.5G   1% /dev/shm
lrm                   1.5G   40M  1.5G   3% /lib/modules/2.6.24-26-generic/volatile
gvfs-fuse-daemon      454G  2.9G  428G   1% /home/jess/.gvfs
```

---

### Post by jamesisin on 2010-01-04
> **WeMade said:**
> So it is safe then to delete the giant partition with ubuntu

This means you will no longer be able to run Ubuntu without also reinstalling it.

---

### Post by jamesisin on 2010-01-04
This line tells me that you have Ubuntu installed on a large partition (probably most of the drive):

/dev/sda1             454G

If you are abandoning Ubuntu you can of course delete this partition.  You should be able to use the Windows installation media to wipe out any and all partitions on this drive.

If on the other hand you are trying to keep an Ubuntu installation while also having a Windows installation, you will want to follow the instructions I have offered above.

---

### Post by WeMade on 2010-01-04
> **jamesisin said:**
> This line tells me that you have Ubuntu installed on a large partition (probably most of the drive):

/dev/sda1             454G

If you are abandoning Ubuntu you can of course delete this partition.  You should be able to use the Windows installation media to wipe out any and all partitions on this drive.

If on the other hand you are trying to keep an Ubuntu installation while also having a Windows installation, you will want to follow the instructions I have offered above.
I love ubuntu but I have to have windows for now, at least on the biggest partition. I can make a smaller partition for ubuntu with the cd after I have successfully installed windows at least I hope.

The windows 7 install didn't give me any formatting options on the drive (ubuntu partition) but all I need to do is delete it without changing it to NTFS and it will be okay?

---

### Post by jamesisin on 2010-01-04
Your assessment is correct enough.

---

### Post by WeMade on 2010-01-04
Thanks Jamesisin and other repliers, I bet i'll be back when windows crashes on me again soon enough!

---

