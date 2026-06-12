---
title: "GParted just ate my hard drive --- please help"
date: 2006-04-17
forum: General Help
---

### Post by kerinin on 2006-04-17
OK, so i recently installed dapper, and my hard drive was starting to get sort of messy with all the partitions, so i decided i'd move some things around, seperate my /home from /, make seperate partition for different chroots, etc  -- the point being that i told GParted to copy my primary Breezy partition to a new location then delete the old version and copy my dapper partition to another location and then delete the old one of it.

Well GParted worked for about 20 minutes, threw about 4 errors (which were blank windows) and then ate both of the partitions i was trying to move.  One is now showing up as unallocated, and the other is showing up as an unrecognized filesystem type.

I've tried using parted to rescue the partitions, but it doesn't find anything.  Please tell me that there's something else i can do - i have a LOT of data on those partitions that i don't want to lose.

Thanks in advance.

---

### Post by handy on 2006-04-18
I can't tell you how, with linux I'm sorry.  

I do believe that there is every chance that you can recover your original partitions, ***_providing the data has not been overwritten._***  

This sort of thing can be done relatively easily in windoze, so I am confident that it can also be done in Ubuntu.

Don't do anything to your drives without good advice first, otherwise you could kill your only chance of recovery.

Good Luck.

---

### Post by Sef on 2006-04-18
Here's a couple of rescue disks you can get if you can burn them somehow:

1) [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

2) [http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/")

---

### Post by kerinin on 2006-04-18
The data should be intact - i was doing the repartitioning from the LiveCD.  I can't exactly boot into anything right now, so all i can do is stare at the empty space in GParted.

---

### Post by plors on 2006-04-18
first i guess you have used a way too old gparted, you really should use the latest gparted and preferably start it from it's own [livecd]("http://gparted.sourceforge.net/livecd.php").
second, it's never a wise idea to pile so much operations onto each other. Granted, gparted offers this functionality, but i always suggest taking it one step at a time.

I think 'gpart' is a good tool to recover lost partitions, good luck!

---

### Post by handy on 2006-04-19
Perhaps you can use a live cd to download & burn those rescue disks?

---

### Post by kerinin on 2006-04-19
OK, finally got my data back.  I used TestDrive, which is included on most of the Knoppix live cds.  It just scanned the drive, let me look at the lost partitions, then re-wrote the partition table.

Now i just need to get grub to boot normally, but that's a different issue and i think i've got it taken care of for the most part.

As for GParted, i was using the Dapper flight 4 LiveCD, so i  can only hope that it was an acceptably current version (considering it's what esspresso uses).  I probably should have taken it a little slower, but it was late and i was tired so i just set it all up and went to bed.  If there's any program that should be debugged, it's a partition manager - there's no excuse for this type of thing happening in my opinion.

Thanks for everyone's help

---

### Post by plors on 2006-04-19
I don't know which version of gparted is on that livecd, but i'm quite sure it's an outdated alpha version. Please check the version and post it here.

thanks

---

### Post by mozetti on 2006-04-19
[QUOTE=kerinin]If there's any program that should be debugged, it's a partition manager - there's no excuse for this type of thing happening in my opinion.[/QUOTE]

Considering that moving large amounts of data, 2 OS's, and re-writing partition tables is both a considerable task and one that occurs at a low level of hardware/software interaction, it's not something to be taken lightly. If it were an easy task, don't you think there would be alot more software out there to do it? As a point of reference, just look how many different media players there are out there.

For future reference, it's best to do these types of operations one step at a time and double-checking things worked correctly instead of setting it up and walking way.

---

### Post by homunq on 2007-10-07
I just had something similar happen...

I was running out of space in my linux partition. my partitions in order were

8G windows, 15G data, 7G linux, 500M swap

I decided to move the swap before the linux, to give the extra 500M to linux. I shrunk data - no problem. Then using the gparted on the 7.0.4 live dvd I tried to delete swap. For some reason gparted didn't wanna, so I did it using sudo -i and fdisk. Reload partitions in gparted - good, it's gone, but the damn automounter mounts hda3. Go back into my terminal and umount it. Now in gparted, create new swap and grow hda3 (ext2) to end of disk. Apply.... and fail. Does the fsck, does the resize-partition, but then somehow can't find the file system to grow it to fit the partition. And so I'm looking at an empty partition.

I had some data on there - not more than days of work since last backup, I realize that a lost partition can mean weeks, months or years lost, but still, stuff I need. So I'd be willing to spend days to recover it.

I'll try the suggestions in this thread and see where they get me.

---

### Post by homunq on 2007-10-07
OK - it's not as bad as I thought. I reboot the livecd and now gparted sees the filesystem on /dev/hda3. But there's still some weirdness - gparted sees the filesystem as having grown, when that step did not even run because the error happened in resizing the partition. I'm inclined to just mount the filesystem, but I don't want to cause further damage - is this safe?

Please help...

---

### Post by homunq on 2007-10-07
Well, I realized that the disk was already ##@$ automounted so I guess it's safe.

So I go back and boot to that partition. But I can't do a graphical login because the partition is still "full". I do a df on it and I see something like "total blocks 1000, used blocks 950, free blocks 0" - obviously the filesystem is in some hosed state of not knowing how big it really is. I'm going to try this from the liveCD: [http://ubuntuforums.org/showthread.php?t=532735](http://ubuntuforums.org/showthread.php?t=532735)

---

### Post by homunq on 2007-10-07
"do a df" = ctrl-alt-f1 to get a terminal, log in, type "df".

---

### Post by MechR on 2008-04-06
> **homunq said:**
> Well, I realized that the disk was already ##@$ automounted so I guess it's safe.

So I go back and boot to that partition. But I can't do a graphical login because the partition is still "full". I do a df on it and I see something like "total blocks 1000, used blocks 950, free blocks 0" - obviously the filesystem is in some hosed state of not knowing how big it really is. I'm going to try this from the liveCD: [http://ubuntuforums.org/showthread.php?t=532735](http://ubuntuforums.org/showthread.php?t=532735)So, how did it go?  Gparted just did something similar to my NTFS partition when I tried extending it.  Windows still boots, but the apparent drive space hasn't increased, even though partition managers say the partition's now bigger.  Tried running error-checking on the drive in Windows, but it didn't fix anything.

Anyone know of a way to fix my problem?


EDIT: Okay, I think I figured it out and fixed it.  (Let me know if I'm still missing something here...)

I was using an old Xubuntu 7.04 Feisty CD.  When I tried to expand my NTFS partition, Gparted kept mounting it in the middle of things, causing the operation to stop with an error.  So next, I tried dismounting the partition right before Applying the change.  This let it resize the *partition* successfully, but then it automounted again and threw an error, preventing the *filesystem* resize step.  I guess I'm lucky I was trying to expand the partition; if I had been shrinking it, I might've lost data on reboot.  Yeesh.

Anyway, I tried the following:
```
sudo umount /dev/sda3
sudo ntfsresize -n /dev/sda3
sudo ntfsresize /dev/sda3
```
That is,

1. Unmount the partition (/dev/sda3 in my case)
2. Do a test run of ntfsresize (whose default action is to expand the filesystem to fit the partition)
3. Once the test run comes out okay, do the actual run

It seems to have worked.  Whew... But I don't think I'll be using Gparted in the future.  What is up with that automounting behavior? #-o

---

### Post by MechR on 2008-04-06
Well, it turns out things weren't entirely smooth; My Windows account profile got corrupted somewhere along the line.  The files were intact, but you couldn't log into the account.  Luckily (again), it was my general-purpose Limited account, and not my Admin account.  I followed these instructions to create a new account and copy the data in:

[http://support.microsoft.com/kb/811151](http://support.microsoft.com/kb/811151)

NOTE: The new account's folder isn't immediately created at the time of account-creation, but rather upon first login. If you manually create the folder, Windows ignores it and creates a different folder for the new profile upon login.  You have to log into the new account once first, so that it creates the account's folder.  Then go back to the Admin account, delete the default files/folders in the new account folder (except for Ntuser.dat, Ntuser.dat.log, and Ntuser.ini), and copy over your old data.

I neglected to delete the new default files before copying over the old files, so I had some unwanted default icons mixed in with my preferred set.  Plus I lost many of my settings, ex. for theme, Start Menu, visual effects, screensaver/power, mouse, registry tweaks, MS Office, 7-zip, Internet Options, etc.  (But I suspect I would've lost them either way.)

Bleah.  A real time-waster, but I'm gradually ironing things back out as I encounter them.

---

### Post by MechR on 2008-04-08
More horror stories, and their solutions :popcorn:

I soon noticed that in Windows Explorer, right-click -> Open With -> Choose Program had stopped working properly.  In the Choose Program window, when I chose Browse to select a program, it wouldn't be added to the list.

Also, this problem only happened while the account was Limited.  If I promoted it to Admin, it would work again, but any changes I made would disappear once I demoted it back to Limited.

I eventually figured out that the access permissions for HKEY_USERS\<SID>_Classes still used the old, corrupted profile's SID.  To fix this, I did:

1. Promote new account to Admin, and log into it.
2. Start -> Run, regedit.
3. Navigate to HKEY_USERS\<SID>_Classes, where <SID> is a long string of numbers.
4. Right-click -> Permissions
5. Add the new account to the group.  (In the Add window, type the account name into the bottom field and click Search to make it find the corresponding account, then add it.)  Optionally, remove the old SID from the group.
6. Give the new account "Full Control" in the checkboxes.
7. Log out and change the account back to Limited.

---

