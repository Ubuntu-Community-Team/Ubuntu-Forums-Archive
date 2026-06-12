---
title: "Formatting and reinstalling dual-boot help needed"
date: 2010-04-02
forum: General Help
---

### Post by lsk3993 on 2010-04-02
Now I'm sure this question has been asked many times and I've even found  [articles]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")  about this exact same thing, but I thought it would be best to make a  thread just to make sure I know exactly what I'm doing.
I now have XP, Windows 7 and Ubuntu (installed in that order) in messy  partitions on my hard drive and I want to get rid of XP and fix the  partitions and reinstall the other two. Can someone just confirm the  order I think I should do them in:

1) Backup everything useful (documents, pictures, Firefox bookmarks, a  list of installed programs...) Anything else I'm missing?
2) Reboot and put in my Ubuntu Live CD and run GParted in a live session  to format the partitions and delete them to make the hard drive all one  block like it was originally.
3) Set partitions for each OS and its programs as well as a shared space  for documents and other files I want to share between the two. (I use  Steam and have about 5 games on it but otherwise no large applications,  how much space should I give Windows 7 and Ubuntu from a 320GB HD?)
4) Install Ubuntu in the partition created for it and put a 4GB swap  file in the shared space
5) Reboot and install Windows 7 in the partition made for it.
6) Set programs to save their documents in folders in the shared space
7) Use the list of installed programs to go about getting back all the  programs you had before

So, is this ok? Am I right in saying I should install Ubuntu before  Windows 7? And which bootloader should I use? (The way I'm doing it Win 7  will install the MBR over GRUB, right?)

---

### Post by conradin on 2010-04-02
Its well known to be easiest to install the winDoze first because the filesystems cant cope with other file-systems. The installer is not robust enough to handle such a task, and offers little info while installing. Once you have the the Doze installed, go back with what ever linux version you want and install, you'll have all sorts of data on what currently exists and options for what you can do with it. Since winDoze has no idea about other filesystems, it doesn't know better than to overwrite any other non-windoze boot paths.  This is also why its best to use grub as the boot loader for the WinDoze. You're right,if you install linux first the Doze will just over write your boot path. Then you can fix that later if you want. My advice is to install the Doze first then linux, only because MS is F***tarded.

---

### Post by lsk3993 on 2010-04-02
> **conradin said:**
> Its well known to be easiest to install the winDoze first because the filesystems cant cope with other file-systems. The installer is not robust enough to handle such a task, and offers little info while installing. Once you have the the Doze installed, go back with what ever linux version you want and install, you'll have all sorts of data on what currently exists and options for what you can do with it. Since winDoze has no idea about other filesystems, it doesn't know better than to overwrite any other non-windoze boot paths.  This is also why its best to use grub as the boot loader for the WinDoze. You're right,if you install linux first the Doze will just over write your boot path. Then you can fix that later if you want. My advice is to install the Doze first then linux, only because MS is F***tarded.
Ah, thank you for the info.
So now instead of using GParted I just use whatever partition manager the Windows installation uses or should I still use GParted?
Also is the idea of making 3 partitions good?

---

### Post by Mark Phelps on 2010-04-02
I would not trust GParted to create the proper partition for installing Win7.  Instead, I would wipe the drive and let Win7 do its own partitioning.  It will create two partitions by default.

Once it is up and working, I would use the Win7 Disk Management utility to shrink the second (OS) partition to leave room for Ubuntu.

Then, I would reboot from the Ubuntu LiveCd and allow it to install in the unallocated space.

When it reboots, if it doesn't offer you a Win7 choice in the GRUB menu, open a terminal and enter "sudo update-grub".  That should find the Win7 install and add an entry to the GRUB menu for you.

When you reboot again, you should have a GRUB menu with choices for Ubuntu and Win7.

---

### Post by lsk3993 on 2010-04-02
> **Mark Phelps said:**
> I would not trust GParted to create the proper partition for installing Win7.  Instead, I would wipe the drive and let Win7 do its own partitioning.  It will create two partitions by default.

Once it is up and working, I would use the Win7 Disk Management utility to shrink the second (OS) partition to leave room for Ubuntu.

Then, I would reboot from the Ubuntu LiveCd and allow it to install in the unallocated space.

When it reboots, if it doesn't offer you a Win7 choice in the GRUB menu, open a terminal and enter "sudo update-grub".  That should find the Win7 install and add an entry to the GRUB menu for you.

When you reboot again, you should have a GRUB menu with choices for Ubuntu and Win7.
Thanks, so you think it would be best to just have two partitions as opposed to three including a shared space?

---

### Post by oldfred on 2010-04-02
If you are dual booting and may want some data available in both I would create a shared NTFS partition to put my entire firefox profile and any other data you want to share.
You can just create that partition and then install in the remaining free space or create your other partitions / (root), swap and separate /home if you want. If you create create the partitions in advance then you have to use manual install and select/choose those partitions and define what they are. 

If most of your data is in /home or the shared data partition root only needs to be 10-20GB, you can make swap the 4GB if that is your memory size and the rest split between /home and shared depending on how much you think you might need for each.

---

### Post by lsk3993 on 2010-04-03
> **oldfred said:**
> If you are dual booting and may want some data available in both I would create a shared NTFS partition to put my entire firefox profile and any other data you want to share.
You can just create that partition and then install in the remaining free space or create your other partitions / (root), swap and separate /home if you want. If you create create the partitions in advance then you have to use manual install and select/choose those partitions and define what they are. 

If most of your data is in /home or the shared data partition root only needs to be 10-20GB, you can make swap the 4GB if that is your memory size and the rest split between /home and shared depending on how much you think you might need for each.
So I should give the Ubuntu partition about 20GB for it and its applications? The thing is I'm not sure how much I'll need for Windows since new games will obviously require more space.
If I partitioned the drive like 'Windows|Shared|Ubuntu' could I then expand both Windows and Ubuntu if needed?

---

### Post by oldfred on 2010-04-03
It is easier to add space at the end of an existing partition. IF you add it at the beginning it has to move the entire partition which is very slow. If you give Ubuntu 20GB and do not store any or much data in the root partition you will not have any problems. Windows needs 10-20% free space to keep working and allow defrag. By the time you run out of space in Ubuntu you will be buying a new large hard drive anyway.

---

### Post by lsk3993 on 2010-04-03
> **oldfred said:**
> It is easier to add space at the end of an existing partition. IF you add it at the beginning it has to move the entire partition which is very slow. If you give Ubuntu 20GB and do not store any or much data in the root partition you will not have any problems. Windows needs 10-20% free space to keep working and allow defrag. By the time you run out of space in Ubuntu you will be buying a new large hard drive anyway.
Oh right, thanks, that makes sense. I guess I'll just have to work out exactly how much Windows needs and give it 10% more plus room for growth.

EDIT: Problem solved, thanks guys ;)

---

