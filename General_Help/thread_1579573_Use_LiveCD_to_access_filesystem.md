---
title: "Use LiveCD to access filesystem"
date: 2010-09-22
forum: General Help
---

### Post by Reddata on 2010-09-22
I'm using Ubuntu 8.04 LTS in a dual boot environment with XP.  Except that I have two hard drives: One with Ubuntu and XP and one with just XP.  The MBR on the XP-only drive has an entry named "Linux" which points to the grub loader for the split drive.  I tried to reinstall windows on its partition on the split drive, but the install process hung and I've never figured out how to make it finish.  I didn't use that partition for this entire episode.

Yesterday I booted into Ubuntu and tried to log in, but immediately after entering username and password I was presented with an error message (full screen, blue background, red "ok" button).  I don't remember exactly what the wordage was but it had something to do with a hard drive error.  I thought I was experiencing hard drive failure, but I hit the reset button and successfully booted into the windows-only installation.  I didn't think the problem was anything more than a random error.

Today I tried to boot into Ubuntu, but immediately after the splash screen I was greeted with BusyBox v1..1..3 with an (initramfs) prompt.  I restarted and tried Ubuntu again and immediately I encountered the grub> prompt (no grub bootloader, no splash screen).  Confused about why the prompts had changed I decided to boot into Windows, but at the welcome screen an error dialog from lsass.exe informed me of an unrecoverable error in the registry: the semi-famous "registry could not read in, write out, or flush."

Next I tried the live CD.  Using the live CD I could access the contents of both of my windows partitions, but not my Ubuntu partition.  Navigating to "FileSystem" using the LiveCD only yields the directories created for the LiveCD session.

I tried again to boot into windows and it worked, so I'm hoping the message from lsass.exe was just a random hiccup.

Right now I'm pretty much only concerned with getting the Ubuntu partition backed up, and then performing a fresh install.  Content from the windows installations is fully backed up.  The fact that using a LiveCD gives me access to the windows partition on the split drive makes me certain that the drive has not physically died.

Using "fdisk -l" produces no output, and "dmesg" gives some errors at the end of the output:

[  310.832172] EXT3-fs: unable to read superblock
[  341.900881] VFS: Can't find ext3 filesystem on dev sda5.
[  887.351098] end_request: I/O error, dev fd0, sector 0
[  899.495785] end_request: I/O error, dev fd0, sector 0
[  899.495795] Buffer I/O error on device fd0, logical block 0
[  911.636348] end_request: I/O error, dev fd0, sector 0
[  911.636359] Buffer I/O error on device fd0, logical block 0
[ 1032.849498] end_request: I/O error, dev fd0, sector 0
[ 1044.999986] end_request: I/O error, dev fd0, sector 0
[ 1044.999996] Buffer I/O error on device fd0, logical block 0
[ 1057.130682] end_request: I/O error, dev fd0, sector 0
[ 1057.130693] Buffer I/O error on device fd0, logical block 0
[ 1146.185858] attempt to access beyond end of device
[ 1146.185872] sda2: rw=0, want=4, limit=2
[ 1146.185878] EXT3-fs: unable to read superblock

My attempts to use the grub> prompt to reinstall grub return an error (error 15, I think?) when I try "find /boot/grub/stage1"

At this point I'm stuck so I'm turning to the community for help or news of doomsday.  Sorry for the long post.  Given the context, anyone have any ideas on where to proceed from here?

---

### Post by robsoles on 2010-09-22
looks like the partition has fallen apart to me.

It might be arduous reading but take a look at [http://www.faqs.org/docs/Linux-mini/Partition-Rescue.html](http://www.faqs.org/docs/Linux-mini/Partition-Rescue.html)

---

### Post by Chame_Wizard on 2010-09-22
Seems like there is something wrong with the HDD or perhaps the entire partition.

---

### Post by Reddata on 2010-09-22
@robsoles  Thanks for the reply.  I'm trying the steps outlined in the HowTo but I'm not having much success.  Probably partly because I don't fully understand his operations with the partitions.

The result of running "sudo /sbin/fdisk -l" is this:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a371a37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       19457    74364885    5  Extended
/dev/sda5           10200       19074    71288406   83  Linux
/dev/sda6           19075       19457     3076416   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23de23dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19456   156280288+   7  HPFS/NTFS
```I'm pretty sure /dev/sda5 is where all my files for linux are stored.  Then I do "sudo fdisk /dev/sda5" and get:

```
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xe5abbc1f.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.


The number of cylinders for this disk is set to 8874.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): 
```I'm a bit afraid to enter anything at the prompt because I don't quite know where I'm supposed to be going with this.  I don't understand how to perform the next steps in the HowTo.  Does anybody know if I've got the right partition (/dev/sda5) and what I should do next to try to mount it?

---

### Post by robsoles on 2010-09-22
Abandon that part of the howto and look for if they use 'df' in that howto at all.

My memory on it is a little shaky but about a year ago I had some hectic problems on a HDD and df was (pretty sure) the sole tool I ended up being able to recover my data with.

try 'man df' in terminal and variations of 'fix partition using df' in Google, post back if you are still stumped after a bit of that.

---

### Post by Reddata on 2010-09-22
They don't use "df" in the HowTo except to determine the end point of a partition.  After reading the documentation resulting from "man df" I found this:

```
This version of df cannot show the space available on unmounted file systems, because  on  most  kinds  of systems  doing  so requires very nonportable intimate knowledge of file system structures.
```Since the partition I'm interested in isn't mounted, does this disqualify df from being used to repair the partitions?

The output at the terminal of just "df" is:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                  1037300     16512   1020788   2% /lib/modules/2.6.24-19-generic/volatile
tmpfs                  1037300     16512   1020788   2% /lib/modules/2.6.24-19-generic/volatile
varrun                 1037300       104   1037196   1% /var/run
varlock                1037300         0   1037300   0% /var/lock
udev                   1037300        84   1037216   1% /dev
devshm                 1037300        12   1037288   1% /dev/shm
tmpfs                  1037300      5504   1031796   1% /tmp
gvfs-fuse-daemon       1037300    101572    935728  10% /home/ubuntu/.gvfs
/dev/scd1              4339608   4339608         0 100% /media/WIC

```None of those entries look like they're large enough to be the /dev/sda5 I'm interested in.

My internet searching hasn't revealed anything very relevant to my case except this: [http://ubuntuforums.org/showthread.php?t=624943](http://ubuntuforums.org/showthread.php?t=624943)

That thread deals with recovering the windows registry, which is relevant to the message from lsass.exe that I received earlier.  I also found this: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) which looks like it might be worth pursuing but I think I need to finish your steps first.

Since df doesn't seem to be showing the partition I'm looking for, what should I do next?  What if I did "sudo fdisk /dev/sda5" again and then "w" at the prompt?  Since the output for it said:
```
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)
```then can I assume the partition table will be fixed by the write operation?

---

### Post by robsoles on 2010-09-22
mmmmh, must be my hazy memory, maybe du was the one that resurrected my partition layout for me and maybe I am wrong about using a sole tool.

Correcting the invalid flag of partition table 4 may correct it to being readable and intact (having your old files) but it sounded, from the output you showed in previous post, like it might make the file-space empty.

---

### Post by Reddata on 2010-09-22
Thanks for your help so far.  I have to go to class now but I'm going to have another crack at this later this evening.  I think I'll try that link that used gparted.

Thanks!

---

### Post by efflandt on 2010-09-22
Don't expect **sudo fdisk -l /dev/sda5** to do anything useful.  fdisk displays or works with partitions on a drive (like /dev/sda).  For example **sudu -l /dev/sda** gives you info about partitions on drive sda.  That tells you what partitions it finds in the partition table, but not whether the data within those partitions is broken or has bad sectors.

You need to fsck a Linux partition to see if there is something wrong with it or whether it can be fixed.  In a terminal type **apropos fsck** to find commands and man pages related to fsck.  For example:

e2fsck (8 ) - check a Linux ext2/ext3/ext4 file system

So then you do **man e2fsck** to check what options are available for that command.

Drives normally reserve some space to automatically map good sectors in place of bad sectors, transparent to you.  If you actually start seeing bad sectors, that is a bad sign that a drive is deteriorating and should be replaced.  If you cannot get anything you need from it quickly, it may deteriorate to the point that everything on it becomes inaccessible.

Note that you usually need to use **sudo** to do things to main system files or the system itself as root.

---

### Post by Reddata on 2010-09-22
@efflandt
I read the documentation for e2fsck and proceeded to do **sudo e2fsck /dev/sda5**.  This is the output I got:```
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Superblock invalid, trying backup blocks...
/dev/sda5 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 1032193 has zero dtime.  Fix<y>? 
```After answering the prompt with 'y' I got this:```
Inode 1032201 is in use, but has dtime set.  Fix<y>?
```I typed 'y' and got:```
Inode 1032201 has imagic flag set.  Clear<y>?
```It kept cycling dtime/imagic back and forth, each time with a different inode.  I thought that it would be a good idea to start over and do **sudo e2fsck -y /dev/sda5**.  However, I think I made a mistake there because I used an escape character (CTRL+Z) to end the fsck.  Now when I try to **sudo e2fsck -y /dev/sda5** I get:```
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?
```It makes sense that the filesystem is now closed off, but how do I reverse the damage I've done by using the escape character?  What should I have used to start over instead of the escape character?  I tried typing 'n' to some of the prompts but that didn't change the cycle.

---

### Post by Darkness Des on 2010-09-22
CTRL+Z is the command to put the current command in the background and pause it. The bg command will activate it again. After that, running the fg command will bring it to the front.

---

### Post by Reddata on 2010-09-22
@Darkness Des
Thanks for the information.  That is not only useful for now but also for the future.

I got e2fsck to release its "hold" on sda5 and decided to use gparted to check the partition for errors.  After gparted did its stuff I now find a new entry under "Places".  It's my beloved Ubuntu partition.  I can now access it, but it's very limited.  For example, I don't have very many permissions, and the Desktop/Documents/Music/Pictures/Video folders are completely absent from /home/florian (florian being the name of my installation).  Those folders are really what I'm doing all this work for, particularly the Documents folder.  Any ideas on how to get access?  Is the use of the LiveCD causing the lower levels of access?  Perhaps now that the partition can be mounted I can fix GRUB and boot into Ubuntu normally?

---

### Post by robsoles on 2010-09-22
Were you using an encrypted home directory?

---

### Post by Reddata on 2010-09-22
Unless an encrypted home directory is a default option somewhere I don't think my directory is encrypted.  If it were encrypted, would I even be able to see the "florian" directory in it?  If I did enable encryption somewhere along the line, how would I go about decrypting the directory's contents?  Is the encryption key tied to my password?

---

### Post by Reddata on 2010-09-23
Now that I can successfully mount the partition I had the bright idea that I could repair GRUB and boot normally.  I then repaired GRUB and it completed setup with some errors with information that they were not fatal.  I rebooted and was greeted with the GRUB bootloader.  I thought everything was a success and selected my distro from the boot menu.  Alas and alack, after the splash screen I encountered BusyBox v1.1.3 with the (initramfs) prompt.  I rebooted and now I'm back on the LiveCD.

I can still access the partition, but as before the important folders are not visible (not even with hidden files/folders showing).  I don't really know what to try next.

Anyone know what causes the bootup to drop into busyBox?  From what little research I've done I think it's because of hardware failure, but I'm not sure.  The bootup appears to be going fine, but right during the splash screen the (initramfs) prompt appears.

I'm finding other instances online of people encountering busyBox, but their cases all seem to be a problem with the liveCD, which strangely is the only thing that is working for me right now.  

Perhaps I could use busyBox to back up my data?  I say that because it seems to have the necessary commands to navigate directories and copy folders.  In that case, how might I go about doing that?

---

### Post by robsoles on 2010-09-23
I am not familiar enough with busybox to help pursue retrieving your data that way but:

If you boot from LiveCD and then issue
```
gksu nautilus
```
in terminal, it will open a graphical file browser as root and nothing will be restricted or hidden from you unless it is encrypted or broken.

While using the file-browser as root please take a great deal of care not to 'step on' anything.

Navigate to your home dir as root and then press [CTRL]+[H] - if you can't immediately do anything with what you can see in the file browser at that point then please take a snapshot of it using print_screen and post your snapshot here.

---

### Post by Reddata on 2010-09-23
Using nautilus does not show anything different than normal File Browser, even /home.  CTRL+H doesn't change anything in the home directory (where /florian is located) but it does show more files in /home/florian.  No folders were shown.  Unfortunately I can't show you a picture of inside /florian because I attempted to navigate to the examples folder and it has caused a very long hang of nautilus.  The whole system is running slowly now, with the CD spun up all the time.  I'm a bit afraid I've "stepped" on something.  

I can still mount the partition, but everything is a bit jerky now.

---

### Post by robsoles on 2010-09-23
Just closing the file-browser that 'gksu nautilus' brings up should remove 'danger' but it may be necessary to return to the terminal you called it from and press '[CTRL]+[C]' to quit the command that started it.

Of course restarting the PC 'n stuff should put you back where you were before you used 'gksu nautilus' if you didn't actually make any changes to anything using the file-browser as root.

---

### Post by Reddata on 2010-09-23
I ended up having to reboot.  Here's the screenshot of the files that showed up after hitting CTRL+H in /home/florian.  Nothing new showed up in just /home.

As you can see, some of my personal files in /home/florian are visible, but up at the top of the file browser the only folder is named "examples."

---

### Post by robsoles on 2010-09-23
That's troubling from a viewpoint of retrieving the data you want to retrieve.

There should be a 'lost and found' folder in the drive/partition that contains your /home directory. View the contents of it (need to be root, pretty sure) and see if any of your missing stuff (or strange entries of size about appropriate for your stuff) are there.

---

### Post by Reddata on 2010-09-23
To me, almost everything under lost+found is "strange."  With over 6000 folders to peruse, I've been hard at work.  Just from semi-random poking around I've actually found quite a bit of my stuff in archived folders, but only a few of the archives will open.  Most give me "Archive type not supported."

I find data of mine pretty well mixed among the files in the directory.  Most of the stuff I've found (particularly music) is stuff that was moved to trash; I rarely empty the trash.  In fact, for this installation I don't think I ever did.  However, I've found a few isolated images that I know were in the Pictures folder, so it's not all trash stuff.

Are there any rules for telling which stuff is relevant to a particular directory?  Every archive I've encountered of interesting size (10 - 100 MB) is unsupported by the liveCD.  Any way of getting the LiveCD to support those archives?

---

### Post by Reddata on 2010-09-23
Well, after much more poking around I have a new problem.  The bright side is that I found all my data: the entire /home/florian folder was in Lost+found under a folder named #1984132.  However, my attempt to backup the most important data up to a 16Gb external flash drive was met with messages such as this: "The file "Checksum.java" cannot be handled because you do not have permissions to read it."

This message is being displayed even though I initialized nautilus using **gksu nautilus**.  It seems that no matter what you do, you can't use a LiveCD to copy the filesystem's data.  The interesting part is that I can open any of the data in question: images, text files, music.  All of it can be opened and used, but not copied.  I don't dare try to edit them.

Is there a way for me to get the correct permissions?  I would have thought that running nautilus as root would be all that was needed to have permissions to copy the files.  Apparently not, so what should my next step be?

I think I can use chown to change the permissions, but I wouldn't know what to change them to.  I do know that the current owner under the permissions tab is simply "1000."

---

### Post by robsoles on 2010-09-23
one or more of these may help:

Gain ownership: [COLOR="Red"](Not stunningly brilliant to use from LiveCD though!)[/COLOR]
```
sudo chown -R myusername:myusergroup /some-folder-path
```

Give everybody all(/most~) permissions (bad under most circumstances but operable if desperate to retrieve data!)
```
sudo chmod -R 777 /some-folder-path
```

[COLOR="red"]Of course you need to change '/some-folder-path' for your actual target and please be careful, re-check your line for typos when using sudo etc.[/COLOR]

---

### Post by Reddata on 2010-09-23
I've tried **sudo chown -R root:root /media/disk/lost+found/#1984132/** and also **sudo chown -R ubuntu:ubuntu /media/disk/lost+found/#1984132/** but both cases give the same error message of "file can't be handled."  Could the error be that I'm putting the files onto an external drive that won't support permissions?

**sudo chmod -R 777 /media/disk/lost+found/#1984132 **doesn't change anything as far as I can tell.  I still can't access the files.

Is there a way to remove permissions completely?  I know that's not very linux-like, but I'd really like to do more than just look at the files.  It probably wouldn't help now that I've changed the permissions around, but perhaps I should focus on getting past BusyBox and boot normally?

---

### Post by robsoles on 2010-09-23
Actually, come to think of it - if you can read the files from the old partition then permissions on the old partition shouldn't be the problem.

ownership and permissions of the destination device could be the problem.

file-system of old partition not being 100% corrected could be the problem as well.

I think fsck needs to complete on that drive before much else is pursued.

---

### Post by Reddata on 2010-09-23
When attempting to run **fsck /media/disk-1** (which is the destination external drive) I get this: ```
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Is a directory while trying to open /media/disk-1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

Is that because the drive is ntfs?  Also important is the fact that I can't even copy files from /media/disk/lost+found/#1984132 to the desktop of the liveCD.  That makes me doubt that the destination is the problem.

---

### Post by robsoles on 2010-09-24
No, don't check destination - I meant the fsck needs to complete on your old partition, the source drive.

Being NTFS (the destination) should make it easily writable - try creating a text document on your destination by creating nonsense in gedit and trying to save to your chosen destination drive.

I've never tried to copy anything to a LiveCD GUI desktop because I don't expect it to work - it is using limited RAM and an optical disk to deliver that desktop so it must have limited space.

---

### Post by Reddata on 2010-09-24
Running **sudo fsck /dev/sda5** appears to go cleanly:```
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda5: clean, 247672/4456448 files, 5091719/17822101 blocks

```

What I'm trying now is to do **sudo su** at the terminal and then **cp -R /media/disk/lost+found/#1984132 /media/disk-1/Documents/SavedByTheBell**.  It appears to be working, but it's taking an awful long time.  Also some files and folders (a couple of the .c files and /.kde4/tmp-florian-desktop) are reported as invalid operations.  Not quite sure what to do with that but it's non-critical so far.  

I think I misnamed my destination folder, but who cares.  I'll post back with the results later.

---

### Post by Reddata on 2010-09-24
Well, it worked.  I ended up with a huge number of hidden (.filename) files on the backup drive but that's okay I guess.  I suppose I could try to recover my installation now that everything important is backed up but I'm really not sure I have the time to invest in this further.  Besides, that's not the subject of this thread.  I need a working copy of Linux for school, and I think the guaranteed fastest way to do that is to do a fresh reformat.

Thanks robsoles for your help while seeing this through to the end.  To recap the things that worked for people who come along in the future:

1.  When signing in I had partition corruption that caused the boot sequence to drop into BusyBox.
2.  While using a liveCD to back up data, I was unable to mount the partition I was interested in.  The solution to this was to open System > Administration > Partition Editor.  Then right-click the offending partition and select "check."
3. After the partition editor had finished, the partition was now mountable.  The new problem was that /home/username on the partition was devoid of the Desktop/Documents/Music/Pictures/Video folders.  The solution was to look in the lost+found folder.  Since lost+found is unaccessible using normal file browser, I used ```
gksu nautilus
```to get access to lost+found.
4. With over a thousand folders to parse, it took a while, but by only looking at folders with more than 10 items I eventually found the rescued /home/username contents.
5. Now that the files had been found the new problem was that the permissions on the LiveCD don't allow graphical copying of files, not even with **gksu nautilus**.  To get around this I used ```
sudo su
``` to get logged in as root.
6. Now logged in as a superuser, I did ```
cp -R /*originatingFolder* /*destinationFolder*
``` This did the trick, and now all my data is backed up.

And that's it.  I'm so sick of staring at this smilie I'm going to stick him in for spite:guitar:

---

