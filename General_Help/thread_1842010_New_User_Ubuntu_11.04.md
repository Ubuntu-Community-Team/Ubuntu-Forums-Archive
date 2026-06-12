---
title: "New User Ubuntu 11.04"
date: 2011-09-10
forum: General Help
---

### Post by ernestj on 2011-09-10
Hello, I am new to Linux and Ubuntu. I have always been a MS Windows user. I have to admit that I LOVE Ubuntu 11.04. I have never used Linux before so I do not know what life was like before Unity. I think it is 100 times better than windows and have made the switch full time. I do have a question. I installed Ubuntu 11.04 and during the partition, it divided my drive into 377gig for Windows and something like 273 for Ubuntu. I was not able to import all of my files into Ubuntu, but can access them through the OS, which shows up. 
Since, I have copied the folders from MS Windows to the Ubuntu folders. I run Luckysync to keep both sides up-to-date. 
I am sure there is a better way to partition my hard drive. 

Any suggestions?

Thanks, Ernie

---

### Post by holycow131415 on 2011-09-10
if you want to keep files in sync, just create a partition that is ntfs so that windows and linux can read from it.

---

### Post by sanderd17 on 2011-09-10
you can mount your windows disk inside Ubuntu. This can be done via the fstab file. To do this, you should make a dircetory (like /mnt/windows) and add the line
```

/dev/sda1	/mnt/windows	ntfs	defaults	0	1

```
to the file /etc/fstab. Off coarse /dev/sda1 should be your windows partition. Don't forget to make a backup of your fstab file before you edit it. If it fails, simply put the backup file back with a live CD.

Than you can make a symbolic link from a Linux directory to the windows partition. Do by executing a command like this:

```

ln -s /mnt/windows/users/holycow/Documents /home/holycow/Windows_documents

```

Where the first part is the path to your windows documents and the second path is the easy path that you want to see in your file manager.

If you have questions, do ask them.

---

### Post by ernestj on 2011-09-10
Thank you for the help. Remember, I am new to this. Can you be a little more detailed on how to do this.

Thanks

---

### Post by sanderd17 on 2011-09-11
Sure.

How is your computer partitioned?

Can you install the app gparted from the software center and launch it?

There you will see all the partitions of your computer. Windows partitions are formatted as ntfs while linux partitions are generally ext4.

So find out how your primary windows partition (your C drive) is called. This will probably be something like sda1 or sda2 in gparted.

Now, remember that name. 

Open the file manager in root mode by pressing ALT+F2 and executing
```

gksudo nautilus

```

BE CAREFULL. You can now edit any file you want. Including system critical file. You will not be warned if you do something wrong.

Now you go to the directory /mnt. There you create a new folder (name it windows_documents for example).

Afterwards, go to the /etc directory and copy the fstab file as a backup. Place it somewhere like in your home directory. Now edit the fstab file (the one inside /etc) and add the line
```

/dev/sda1	/mnt/windows	ntfs	defaults	0	1

```
Where sda1 is the name of your windows partition that you remembered from gparted.

Then reboot. 

If you aren't able to reboot, you should boot a live CD or USB and restore the backup fstab file to /etc.

If you can reboot, you should be able to access your windows disk through /mnt/windows_documents (via the regular file manager). If this is not the case, please give us some info (how does your fstab file look like, a screenshot of gparted, what do you get instead ...)

If you can access your windows documents there, than you can create a link from your home to your windows documents.

Do that with the command
```

ln -s /mnt/windows_documents/users/holycow/Documents /home/holycow/Windows_documents

```

where the first path is the one you can use now, and the second one is the one in your home directory that you want to use for easy access.

---

### Post by ernestj on 2011-09-12
Ok. I will explain this as best as I can. I bought a new ASUS with Windows 7. Got Ubuntu 11.04 Live CD and installed. During the installation, it said that it was going to partition the hard drive 377gigs for Windows and 273gigs for Ubuntu. Not knowing any better I clicked ok and completed the installation. Now, I know that there is a better way to have this partitioned. I have been able to access my files through Ubuntu (i can access the whole drive from Ubuutu) that were originally saved in Windows (before Ubuntu install). I brought the main files that I use and saved them in the Ubuntu Documents folder. 
What is the best way to partition and use Ubuntu 99.9% of the time, but can boot Windows and use Windows when I need it. It there a way to have a certain amount of gigs for Ubuntu and an amount for Windows and then have my files on the rest of the drive? Do I use Gparted to fix this?

---

### Post by rwakc on 2011-09-14
If you want to access your files from ubuntu as well as from windows, than the easiest way is to save files on your windows partiton, but keep in mind, that the space you have on ubuntu partiton will be left unused witch is not good.

So I suggest you to do the next:
- Install GParted
- unmount your windows partiton(if it is mounted)
- rightclick on windows partiton in GParted and choose Move/Resize and resize your partiton so that you will have about 20Gb of free space left, in case you want to install anything in windows(You can live more or less than that)
- press apply all operations button(green tick)

Now probably the easiest way to do it, since you can not resize your root partiton, would be to make a bootable usb with ubuntu using Startup Disk Creator and then resize your partiton from the OS running on your usb. Resizing is the same as for windows partition. I recommend you live about 30-50Gb for ubuntu entirely.

If everything went well, you should now have a lot of unallocated space. You will use this space for your data. Rightclick the unallocated in gparted and click new. Choose the NTFS file system, so that both(windows and ubuntu) can read it.

Now that is about it. You will now have three partitons so in case you want to format your windows or linux partiton your data remains intact.

If you want for your partiton to automount when you log into ubuntu, than I recommend you use pySDM(Storage Device Manager) which you can find in Ubuntu Software Center.
Try to mount and unmount partitions, so that you find out which one is the one you just created for the data. Use the assistant button for easier settings.

---

### Post by Mark Phelps on 2011-09-14
Personally, I would STRONG recommend against using Windows to share files with Ubuntu.  Win7 especially, is sensitive to filesystem corruption when its files are updated from OUTSIDE -- which is the case when you have the OS partition mounted read/write in Ubuntu.

A much SAFE way to go is to migrate all the files you want to share to a single NTFS data partition.  Then, once you have the file there, confirm that you can access them from Ubuntu.

If that works OK then go back into Win7 and use the Disk Management utility to shrink down the Win7 OS partition.  Do NOT use GParted to do this because, as I have said, Win7 is touchy about its filesystem being messed with from outside.

Also, since you mentioned that you want to continue to use Win7, then do yourself a favor, boot into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  That will come in handy later should you need to boot Win7 from CD to make repairs.

Also, once you have Win7 shrunk down to where you want it, then use the Free version of Macrium Reflect to image it off to an external drive.  That way, you can easily restore it later -- should you need to do that.

---

### Post by sanderd17 on 2011-09-14
Do you want your files to be accessible for Windows?

**If you don't:**

From a live OS:

Shrink the Ubuntu and windows partition so that you have about 25% free space on those partitions. Make sure that the new empty space is connected (so that you don't have two parts of empty space).

Create a new partition (formatted as ext4) that will become your /home directory.

Move the files from your ubuntu installation and your windows installation to your new partition. Remember that it will become the /home directory. You files should be under /home/username, so you need to make a directory with the name "username" in which you put your files. Hint: all settings are stored in hidden files inside your /home/username directory. To view the hidden files in Nautilus, press CTRL+H.

Now shrink the Ubuntu and Windows partitions agian, so that Windows is 20 GB (bigger if needed) and Ubuntu should certainly have enough with 15 GB.

The new partition has gotten a name in gparted (something like sda6 or sda7), remember that name and add a line like this to your /etc/fstab file on your ubuntu partition

```

/dev/sda6 /home ext4 nodev,nosuid 0 2

```

Use the name of the correct partition, sda6 is just an example here.

Now you can reboot your computer and you will have plenty of space for Ubuntu with the programs and plenty of space for your documents and settings on your /home partition.


**If you do need to have your files accessible by Windows:**

Than you need to create two partition instead of one: a ext4 as /home (since your settings need to be on a native Linux partition, so no ntfs) and you need to create another ntfs partition for your data (since Windows can't read from native linux partitions).

You can create the /home partition and mount it as described above (you just don't have to make it as big) and you can create the ntfs partition for your data and mount it as described in my previous post.

**Do watch out**

Make drawings of what you want to achieve before you start, and note the names of the partitions while you are progressing on those drawings. So that you know what you are doing.

Backup any files you edit (by renaming them with a .backup after it before you start editing them)

Never interrupt gparted, if you do that, you will lose all files on the partition that is being edited.

Do one task (a shrink, new partition creation, enlarge ...) at a time.

---

