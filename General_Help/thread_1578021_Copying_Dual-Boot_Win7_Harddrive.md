---
title: "Copying Dual-Boot Win7 Harddrive"
date: 2010-09-19
forum: General Help
---

### Post by Wingzero54 on 2010-09-19
Hello ubuntu forums,

My brother has been a long time Linux fan, and has been getting on me forever to dual-boot my computer with Linux.  So I finally got around to it and dual-booted it with a partition, and it works just fine, problem is all my stuff is on the Windows 7 partition of the hard-drive.  I hear the big Linux feature is being able to take everything from the Windows side of the computer and transferring it over to the Linux side...

My only question is, where would I find that feature?  I browsed around the administration system capabilities but couldn't find anything related to the partition, so I could use a little guidance in finding the feature, or whether I need to download a program to use it.

Thanks!

P.S. I looked through a couple different forum sections and couldn't find a thread about this... Sorry if it's out there somewhere already!

---

### Post by robsoles on 2010-09-20
Welcome to UF.


It is a feature of the installer to 'grab' your windows documents and 'stuff' to import into your new Ubuntu Linux installation but 

(1) I am not sure they have made it ready and compatible with Windows 7 yet (I am probably wrong about this but am unsure to be honest)

(2) I think the option is only offered during installation and cannot be called upon later - it is only offered if the installer finds **definite** hits of files that are good to import.


Every time someone posts to your thread it goes back to the top of a list of threads that are active right now giving it a chance to be viewed by someone else who may know better.

Wait a while and then post back on this issue if nobody comes in with a better response than mine - who knows, I might come back with a better response if I happen to purposefully or even accidentally research this a little more.

---

### Post by Mark Phelps on 2010-09-20
> **Wingzero54 said:**
> ..I hear the big Linux feature is being able to take everything from the Windows side of the computer and transferring it over to the Linux side...
Never heard of such a "feature" that will take "everything" from any MS Windows OS and transfer it to Ubuntu.

However, when you do the initial install, there is a feature to import some stuff from your MS Windows account into your Ubuntu account.  That may be what you heard about.

IF you want to share files between Win7 and Ubuntu, since MS Windows can't (Currently) read Ext4-formatted partitions, your best bet would be to create a separat NTFS-formatted data partition, move your shared files into there, and use that.

I would create the partition by doing the following:
1) Use the Win7 Disk Management utility to shrink the Win7 OS partition to make room for a new partition.  Do not use Ubuntu or GParted to do this.
2) Create the new NTFS partition using the same Win7 Disk Management utility.
3)Using Win7 file manager, copy the files you want shared into the new partition.

Boot into Ubuntu, use Places to open the new partition, confirm that you can see and use the files.

IF you now want the space removed from your Win7 OS partition (the space those files were using), then do the following:
1) Go back into Win7
2) Use the Win7 file manager to remove the files
3) Use the Win7 Disk Management utility to shrink the partition.

After that, you will have unallocated space on your drive.

Depending on how the partitions are arranged, you may need to boot into a GParted LiveCD to "move" the Ubuntu partition to the left (if that's where the new unallocated space resides), and then use the Win7 Disk Management utility to expand the new NTFS data partition to take up the new unallocated space brought about by moving the Ubuntu partition to the left.

---

### Post by Wingzero54 on 2010-09-20
Okay, wow, that's a little over my head but when I get some free time I'll definitely look into that.

Thanks a bunch!

---

### Post by SeijiSensei on 2010-09-21
The simplest solution is just to mount the Windows partition on Ubuntu.  Try this.  Open the Terminal application, then type

sudo mkdir /media/windows 
Enter your password when prompted

If, as is likely, your Windows ("NTFS") partition is the first one on the disk, try typing

sudo mount /dev/sda1 /media/windows

You should now be able to see the entire Windows filesystem by viewing the contents of /media/windows.  Usually you'll find your personal files in /media/windows/Documents and Settings/yourusername.

I'm running Kubuntu 10.10, the current development version of the KDE flavor of Ubuntu.  If I open "dolphin," the file manager equivalent to Gnome nautilus, it lists all the available file systems in the left-hand column.  In my case, there's an entry for "19.1 GB filesystem"; when I double-click that, I see my Windows partition without any of the command-line mounting required.

---

### Post by robsoles on 2010-09-21
When using the desktop version of Ubuntu most 'mountable' media turns up under 'places' and it is not necessary to use terminal to mount them.

---

