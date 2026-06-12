---
title: "Removing Ubuntu Netbook Remix"
date: 2009-10-26
forum: General Help
---

### Post by teward on 2009-10-26
Okay, here's a question.  A friend installed ubuntu netbook remix, and wants to remove it now.

How would I go about doing this for my friend?

---

### Post by prem1er on 2009-10-26
Remove it and install windows? Just insert the Windows disk and install normally. Format the drive Ubuntu was on during the Windows install and Ubuntu will be removed.

---

### Post by BigG123 on 2009-10-26
Just reinstall it.  The default Grub2 install will rewrite it and reconize Windows.

---

### Post by flipper9 on 2009-10-26
Do you mean he wants to goto the regular Ubuntu desktop, or back to Windows XP?

---

### Post by teward on 2009-10-26
> **TrekCaptainUSA said:**
> Okay, here's a question.  A friend installed ubuntu netbook remix, and wants to remove it now.

How would I go about doing this for my friend?

Perhaps I should have been clearer:

There are two OS installed simultaneously on the drive:  WinXP and Linux.

The friend would like for me to nuke the Linux part, and resize the XP part to fill the whole drive.

I can do this using a partition manager that I have (I'm a tech, btw, and I service mostly windows computers) via the windows partition, and nuke the Linux partition, or I can use a community-approved way of getting rid of Linux but leaving the rest of the drive intact.

---

### Post by Finalfantasykid on 2009-10-26
You should be able to delete the linux partition and reformat it to something windows can recognize(ntfs for example).

However I don't think you can simply resize the windows partition.  You might have to have windows use two partitions, one can just be storage and such.

And for how you would do this, is by booting into Ubuntu using a live CD, and using GParted to do all the partitioning.  This would be the method that I would trust the most.

---

### Post by teward on 2009-10-26
> **Finalfantasykid said:**
> You should be able to delete the linux partition and reformat it to something windows can recognize(ntfs for example).

However I don't think you can simply resize the windows partition.  You might have to have windows use two partitions, one can just be storage and such.

And for how you would do this, is by booting into Ubuntu using a live CD, and using GParted to do all the partitioning.  This would be the method that I would trust the most.

Small problem:  They don't have a CD drive, and erased the flash drive they used to install the software.

---

### Post by mechro on 2009-10-26
> However I don't think you can simply resize the windows partition. You might have to have windows use two partitions, one can just be storage and such.

If TrekCaptainUSA has a fully featured "partition manager" then there shouldn't be a problem resizing.

The MBR may need restoring to a Windows MBR.

---

### Post by teward on 2009-10-27
> **mechro said:**
> \The MBR may need restoring to a Windows MBR.

That's the only thing I'll need to figure out.  Seeing how it's a netbook, I can't use a CD for it, but oh well.  Google is my friend.  :)

---

### Post by cariboo on 2009-10-27
Have a look at [Unetbootin]("http://unetbootin.sourceforge.net/"), another good tool to add to your technicians toolkit.

---

### Post by teward on 2009-10-27
Thanks for all the help, people!

---

### Post by teward on 2009-10-27
> **mechro said:**
> If TrekCaptainUSA has a fully featured "partition manager" then there shouldn't be a problem resizing.

Final note before I mark this topic solved:

Since I'm a tech, and I got the software Paragon Partition Manager Professional Edition, I checked, and I can resize and delete partitions.  It even recognizes all Linux partition types.  So there won't be a problem with this.

---

### Post by StygianAgenda on 2011-06-09
I know this is marked SOLVED, but I do this process fairly regularly for people, when I do a full replacement of their existing Linux with a different build or newer distro, etc.

1. Download "Gparted bootable ISO" (newest is fine; older if needed).

2. Boot into Gparted and fix up your partitions.

3. reboot computer to Windows XP installation CD and when prompted, drop to the command line recovery console.

4. run: fixboot c:
5. run fixmbr c:

6. reboot into XP.

Note: the Gparted bootable ISO is basically similar to the other partition manager that you mention, but it's completely opensource license, so it's free to use, copy, distribute, etc.  The 2 commands I listed here from the Windows XP CD can be ran in any order.  Of course, the usual /? works for getting the usage syntax, if you need further reference, or if my memory of the commands is off (I'm reciting all of this from memory).

Best of luck, m8. ;)

---

