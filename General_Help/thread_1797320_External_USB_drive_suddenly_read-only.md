---
title: "External USB drive suddenly read-only?"
date: 2011-07-04
forum: General Help
---

### Post by carbon512 on 2011-07-04
Been happily going along with Lucid Lynx, locked in, no problems. Slowly  sorting through many files on an external 500 GB USB drive, moving into  useful sub-folders. Today, I cannot write to any folders on that drive  -- read only. ?!?! I run nautilus as root, still no joy. (Using nautilus  GUI to browse files to move to other folders..  am a GUI fan anyway,  sorry..)

No idea what caused this to happen -- how can I change  these settings to allow me to  be able to write to this drive again?  Some terminal command... xxrrww  ... agh sorry.

---

### Post by bdentremont on 2011-07-04
> **carbon512 said:**
> Been happily going along with Lucid Lynx, locked in, no problems. Slowly  sorting through many files on an external 500 GB USB drive, moving into  useful sub-folders. Today, I cannot write to any folders on that drive  -- read only. ?!?! I run nautilus as root, still no joy. (Using nautilus  GUI to browse files to move to other folders..  am a GUI fan anyway,  sorry..)

No idea what caused this to happen -- how can I change  these settings to allow me to  be able to write to this drive again?  Some terminal command... xxrrww  ... agh sorry.

Drives in Windows and Mac formats can become read-only to Linux if they are removed uncleanly (i.e unplugged or powered down without warning) from their respective native operating systems.  If your drive is indeed in a Windows format (i.e. NTFS) plug it into to a Windows computer, open it up, then disconnect it cleanly (using the remove hardware function in Windows).  Then try again in Ubuntu.

Unfortunately, there are no really good choices of format for your drive if you also use Windows, since Windows doesn't read Linux formats at all.

---

### Post by carbon512 on 2011-07-05
hmm no success. I booted in to Windows but Windows would not mount it -- saw it as a device, so I tried ejecting it, rebooting.. no luck. back to Windoze, still would not mount as drive but tried "disabling" it; back to Ubuntu, still read-only. Owner is #99; can't change that..

I wll try mounting it on a Mac tomorrow but am pretty sure I opted for a Windows/Linux readable format (since I do have Windows on this netbook), not a Linux/Mac format.

Is there some way I can change the permissions in terminal?This is a bummer, losing write access to a 500 GB drive! (I guess I could copy all the data off and reformat but.. oy...)

---

### Post by Toz on 2011-07-05
What filesystem did you use? (NTFS, Fat32)?

Open a terminal window, plug in the device, then type:
```
dmesg
```
Post back the last 10-15 lines

Then type in:```
sudo fdisk -l
```and post back the results.

If its a Fat filesystem, you can run:```
sudo dosfsck -v /dev/xxx
``` (where xxx is the device name) to run a check on the drive.

---

### Post by bdentremont on 2011-07-05
> **carbon512 said:**
> ... Owner is #99 ...

Is there some way I can change the permissions in terminal?This is a bummer, losing write access to a 500 GB drive! (I guess I could copy all the data off and reformat but.. oy...)

I'm not sure I like the #99 thing.  If I mount a drive, it comes up as owned by my user name, not number.  You may indeed have a simple permissions problem and we can fix that.

Please try the following in your terminal, and post the output:
```

ls -la /media

```

However, I also think it's likely you have a file system problem, which can be pursued along the lines of what toz suggested.

---

### Post by carbon512 on 2011-07-05
> **bdentremont said:**
> I'm not sure I like the #99 thing.  If I mount a drive, it comes up as owned by my user name, not number.  You may indeed have a simple permissions problem and we can fix that.

Please try the following in your terminal, and post the output:
```

ls -la /media

```However, I also think it's likely you have a file system problem, which can be pursued along the lines of what toz suggested.

that returns:
```

total 12
drwxr-xr-x  4 root root 4096 2011-07-04 22:05 .
drwxr-xr-x 21 root root 4096 2011-03-19 14:20 ..
drwxrwxrwx  1   99   99   20 2011-06-19 14:56 BIggirl
lrwxrwxrwx  1 root root    6 2010-04-19 11:32 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2010-04-19 11:32 cdrom0
-rw-r--r--  1 root root    0 2011-06-08 21:42 .hal-mtab

```The "Biggirl" with the 99 99 is the one in question... I did have changed permissions issues once before with an external drive I had used on a Mac, but I was able to mount it on that Mac and  simply change permissions there... 

So I am thinking/hoping I can change the permissions? I should know what those above permissions mean, but... use it or lose it... and I don't use it, so,,,

---

### Post by carbon512 on 2011-07-05
> **Toz said:**
> What filesystem did you use? (NTFS, Fat32)?

Embarrassed to say I cannot remember. Spent a great deal of time researching and deciding since I use Mac, Ubuntu and occasionally Windows. Aha I do recall now that I formatted it to be best for OSX and Linux; didn't care about Windows.

>  Open a terminal window, plug in the device, then type:
```
dmesg
```Post back the last 10-15 lines ```
 4853.474043] usb 1-1: USB disconnect, address 2
[ 4895.200147] usb 1-1: new high speed USB device using ehci_hcd and address 3
[ 4895.350082] scsi7 : usb-storage 1-1:1.0
[ 4896.390737] scsi 7:0:0:0: Direct-Access     ST950032 5AS                   PQ: 0 ANSI: 2 CCS
[ 4896.391661] sd 7:0:0:0: Attached scsi generic sg1 type 0
[ 4896.393728] sd 7:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[ 4896.395917] sd 7:0:0:0: [sdb] Write Protect is off
[ 4896.395924] sd 7:0:0:0: [sdb] Mode Sense: 34 00 00 00
[ 4896.395929] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 4896.400282] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 4896.400294]  sdb: sdb1 sdb2
[ 4896.725538] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 4896.725547] sd 7:0:0:0: [sdb] Attached SCSI disk
[ 4897.243428] hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.
```> Then type in:```
sudo fdisk -l
```and post back the results.```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe197e31e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1567    12582912   27  Unknown
/dev/sda2   *        1567        1580      102400    7  HPFS/NTFS
/dev/sda3            1580       23873   179072433+   7  HPFS/NTFS
/dev/sda4           23874       30401    52436160    5  Extended
/dev/sda5           23874       30128    50243256   83  Linux
/dev/sda6           30129       30401     2192841   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa973ff7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488386583+  ee  GPT
```> If its a Fat filesystem, you can run:```
sudo dosfsck -v /dev/xxx
``` (where xxx is the device name) to run a check on the drive.So, is it NTFS? Or is that just the partition on my internal drive? Confused. Thanks for this help.

---

### Post by wildmanne39 on 2011-07-05
Hi, it looks like the usb drive is 500 gig drive it says it is GPT but I am not familiar with that, so we will wait for someone that knows that partition system to show up.

---

### Post by mikejonesey on 2011-07-05
strange try;

sudo mount /dev/sd?1 /media/myusb
sudo chown -R normuser:normuser /media/myusb64
sudo chmod -R 764 /media/myusb64

maybee this will force the drive to be readable again file by file?

---

### Post by hawthornso23 on 2011-07-05
```
[ 4897.243428] hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.
```

This line seems to suggest the solution. Have you tried doing what it says?

---

### Post by Toz on 2011-07-05
You will need to have the package hfsprogs installed to run fsck.hfsplus:```
$ apt-file search fsck.hfsplus
[COLOR="Red"]hfsprogs[/COLOR]: /sbin/fsck.hfsplus
[COLOR="Red"]hfsprogs[/COLOR]: /usr/share/man/man8/fsck.hfsplus.8.gz
```
If not already installed, install it through the Software Centre or via:```
sudo apt-get install hfsprogs
```

Then you can check the drive:```
sudo fsck.hfsplus /dev/sdb1
```
and/or try to repair the catalog file:```
sudo fsck.hfsplus -r /dev/sdb1
```

Reference:[http://linux.die.net/man/8/fsck.hfsplus]("http://linux.die.net/man/8/fsck.hfsplus")

---

### Post by bdentremont on 2011-07-05
> **carbon512 said:**
> Embarrassed to say I cannot remember. Spent a great deal of time researching and deciding since I use Mac, Ubuntu and occasionally Windows. Aha I do recall now that I formatted it to be best for OSX and Linux; didn't care about Windows.

No problem, the output you've given us is sufficient verify that the drive is HFS+ and I get this problem sometimes too with HFS+ drives.  I'd suggest that you plug the drive into your Mac and remove cleanly as I suggested with Windows, this alone will probably resolve your problem.

However, while you have the drive on your Mac, I'd let OS X check a couple of things on it's own file system. Select Disk Utility (From Applications/Utilities) and ask it to "verify" the drive.  Also, select the partition and look at the details at the bottom of the Disk Utility screen. Make sure that it the format is something like "Mac OS Extended" or "Mac OS Extended (Case-sensitive)" but NOT Mac OS Extended (Journaled)".  Turning Journaling on will also make the drive read-only to Ubuntu, but I doubt that's the problem, if the drive has worked in the past and you didn't.

Regarding the file permissions, the HFS+ formatted drives do carry UNIX file permissions and the 99 is very much in keeping with what permissions set by OS X look like in Ubuntu.  The file permission you listed should be OK as long as all the sub-directories are set the same, since everyone can read and write regardless of ownership.

---

### Post by carbon512 on 2011-07-05
> **bdentremont said:**
> No problem, the output you've given us is sufficient verify that the drive is HFS+ and I get this problem sometimes too with HFS+ drives.  I'd suggest that you plug the drive into your Mac and remove cleanly as I suggested with Windows, this alone will probably resolve your problem.

However, while you have the drive on your Mac, I'd let OS X check a couple of things on it's own file system. Select Disk Utility (From Applications/Utilities) and ask it to "verify" the drive.  Also, select the partition and look at the details at the bottom of the Disk Utility screen. Make sure that it the format is something like "Mac OS Extended" or "Mac OS Extended (Case-sensitive)" but NOT Mac OS Extended (Journaled)".  Turning Journaling on will also make the drive read-only to Ubuntu, but I doubt that's the problem, if the drive has worked in the past and you didn't.

Regarding the file permissions, the HFS+ formatted drives do carry UNIX file permissions and the 99 is very much in keeping with what permissions set by OS X look like in Ubuntu.  The file permission you listed should be OK as long as all the sub-directories are set the same, since everyone can read and write regardless of ownership.

Thank you so much. This was exactly the issue, I did that this morning and voila, success. (I now recall having to do a forced unmount of that drive from the Mac some time ago.. so that did it.) Went back after reading this and double-checked and, yes, it is NOT Mac OS Extended (Journaled).

Some other questions about who has ownership of the drive - the last Mac to see it appears to be claming it -- but I want to explore on my own first and don't have time now. May re-open this thread later for this related discussion if I have more questions on it.

Appreciate everyone's helpful info.

---

### Post by bdentremont on 2011-07-05
> **carbon512 said:**
> Some other questions about who has ownership of the drive - the last Mac to see it appears to be claming it -- but I want to explore on my own first and don't have time now. May re-open this thread later for this related discussion if I have more questions on it.

I'm glad you got that working!  As a OS X/Ubuntu dual booter, I'll go ahead and take a  stab at letting you know where you stand with ownership, but I'm not really recommending more action at this time for your use of the external drive.  To fully understand it you'll need to study the function of the "chown", "chmod", and "ls" commands.

The problem with ownership is not that one computer claims the drive, but that each directory and file on it is owned in the name of a particular user, which is identified by number (UID) on that machine.  Even if your user name on the Mac and Ubuntu are the same, the UIDs are assigned by a different sequence, so the directory shows up on Ubuntu as owned by user #99, but Ubuntu doesn't have a user name associated with user #99.

Your drive works, despite the absence of a known owner, because the permissions (set with "chmod") are sufficiently lenient to allow anyone to do anything.  To assign ownership of the drive *and everything in it* to yourself, you would use

```

sudo chown -R yourusername /media/BIggirl

```

However, you will have the reverse problem when you get back to the Mac, and I don't particularly recommend doing that unless you have a particular plan for how you want to lock down the permissions.

It is possible to set the UID of your user account in Ubuntu to match that on your Mac and lock down the file permissions to a particular user, as I have done based on the instructions in [[COLOR="Blue"]_this article_[/COLOR]]("http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems"), when I got my Mac so I could seamlessly share date in the OS X home directory. However, tinkering with this on drives and OS installations you have a lot invested in, particularly if you don't understand the Unix permissions, could get a world of hurt really fast. :-)

---

### Post by carbon512 on 2011-07-09
I have not had a chance to read and dig around more in the permissions area, since I got everything working and have been busy... have read about "chown", "chmod", and "ls" commands but not ready to start playing with them.

But this is a concern -- today the drive just stopped while playing music. Disappeared -- not a clean unmount. It is old and operates in a dusty environment but I was able to replug it in and get it running again, on borrowed time no doubt...

Drive reverted to read-only, with same message returned from dmesg - not unmounted cleanly. No surprise.

BUT even after cleanly unmounting the drive, safely ejecting, etc. -- a few times -- it remained read-only until I mounted it and unmounted it on the Mac (I had not even plugged it into a Mac since fixing it). That did fix it, but --

This could be a problem when I don't have a Mac handy. Is this to be expected? Will poking around in permissions for the drive itself when I have time, and locking them down, solve this eventually? Can't play with sharing OSX/Ubuntu account names etc. yet since I wont be at my own Mac for several more months and can't really do that on work editing computer...

---

### Post by bdentremont on 2011-07-09
> **carbon512 said:**
> ... This could be a problem when I don't have a Mac handy. Is this to be expected? ...

Yes.  If my dual boot system crashes in Linux, thus uncleanly unmounting the my HFS+ non-journaled partition, it becomes read-only to Ubuntu until I boot OS X.

No about of file permissions tinkering will fix this. This particular problem is about how the filesystem drivers mount the drive (read-only or not), not whether you have access to it.

If there is an in-Ubuntu solution to fixing the unclean unmount, it's probably fsck.hfsplus, as suggested by Toz.  I'm going to  make a throw-away partition on a flash drive and try it since, for obvious reasons, this interests me too.  I'll let you know what I find.

---

### Post by carbon512 on 2011-07-09
Thanks, I'll keep an eye out for what you discover and get back to tinkering this fall (when I finally upgrade to Natty, too... on the "only as needed" route right now, locked down with something that works well).

---

### Post by bdentremont on 2011-07-09
> **carbon512 said:**
> Thanks, I'll keep an eye out for what you discover and get back to tinkering this fall (when I finally upgrade to Natty, too... on the "only as needed" route right now, locked down with something that works well).

The command fsck.hfsplus, previously suggested by Toz, works great and will be useful to me as well.  Here's what I did

Installed the tool:
```
sudo apt-get install hfsprogs
```

Listed mounted partitions and identified the one that was giving me trouble by block device name, in my case /dev/sdc1:
```
df -h
```

Unmounted:
```
sudo umount /dev/sdc1
```

Ran fsck.hfsplus:
```
sudo fsck.hfsplus /dev/sdc1
```

Clicked on the drive in the Nautilus file manager (or remove and reinstall) to re-automount the drive.

Note that block device names for removable devices will change, so look before you umount.

I'm still running Maverick as well until my doctoral dissertation is out in a couple weeks.  Bad time to crash the computer as far as I'm concerned :-).

---

