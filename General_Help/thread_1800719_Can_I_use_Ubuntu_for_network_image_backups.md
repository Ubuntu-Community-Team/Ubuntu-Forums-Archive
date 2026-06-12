---
title: "Can I use Ubuntu for network image backups?"
date: 2011-07-09
forum: General Help
---

### Post by walterbyrd on 2011-07-09
My home network:

My desktop: Ubuntu 10.10 64-bit
My laptop: Windows 7 64-bit no OEM disk
Wife's desktop: Windows XP

My desktop has two 500GB drives, which is over 900GB more than I currently use. 

I would like to be able to make backup images of my windows boxes, save the images on my Unbuntu box, and be be able to restore those images, if I need to do so. An automated method to update those images on a regular basis, over the network, would be a bonus. 

BTW: I deeply resent HP/Microsoft not providing OEM disks, especially since the Windows 7 built-in utilities to create/restore images is completely borked.

---

### Post by yuler on 2011-08-29
Yes, but I can only get you part way there using the default Bash shell.   There's several ways, but the principle behind  cloning a hard disk is to disable use while being read.  

**Method #1: Backup over an open network**

Tell your Ubuntu machine to listen for the backup datastream:

```
netcat -l -p 1234 | bzip2 > partition.img
``` 
On source (Windows) machine, boot to a Ubuntu LiveCD and go to terminal:

```
dd if=/dev/hda | netcat < targethost-IP > 1234
```**Method #2: Backup over a secure network**

[Setup a SSH server on the host (Ubuntu) machine.]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring")

On the Windows machine, boot to a Ubuntu LiveCD:

```
dd if=/dev/sda | ssh -p 1234 <username>@<IP> "sudo bzip2 > partition.img"
```**Trim the Fat**
Depending  on how much space has been used over the life of the disk, you may to  wipe unused space (convert to zeroes) before sending the datastream, as  repeating a single number compresses  well.

```
dd if=/dev/zero of=WIPE_FILE; rm WIPE_FILE
```Then, just string the sequences together:

```

dd if=/dev/zero of=WIPE_FILE
rm WIPE_FILE
dd if=/dev/sda | ssh -p 1234  <username>@<IP> "sudo bzip2 > partition.img"

```Save it to a file like "remotebackup.sh", so you need only type it instead of the commands.

[SIZE=2]**Improvements**[/SIZE]

[LIST]
[*]Code a filename generator instead of "partition.img".
[*]Store a  Linux ISO image on the Windows machine and boot to it instead of a  LiveCD.  You'd have to replace the Windows bootloader with GRUB2 (or the  like).
[*]Boot to Linux on a thumbdrive.
[/LIST]
   There may be a way to remotely boot to the Linux OS on the Windows machine, but I don't know how.  Maybe someone else can chime in.  If you did, you could initiate the backup script from the Ubuntu machine  manually or through a schedule (cron) and script the entire event.

Hope this helps.

---

### Post by SeijiSensei on 2011-08-29
Isn't it easier to share the Windows hard drives and mount them on the Ubuntu box with smbmount?  Then use rsync to copy from the mounted drives to the backup area.

To insure full coverage you'll need to share C:\ on each machine.  You'll also need to install the smbfs package to get the smbmount utility.

```

sudo apt-get install smbfs
sudo mkdir /mnt/winxp
sudo mkdir /mnt/win7

smbmount //mymachine/C /mnt/win7
smbmount //wifesmachine/C /mnt/winxp

cd /mnt/win7
rsync -av . /media/backup/win7
cd /mnt/winxp
rsync -av . /media/backup/winxp

umount /mnt/winxp
umount /mnt/win7

```

You may need to create entries in /etc/hosts for "mymachine" and "wifesmachine" or use IP addresses in the smbmount command instead.  You may also need to add "-o username=xxx,password=yyy" to authenticate to the Windows machines.  See "man smbmount" for details.  I often use the "-o credentials" option to authenticate instead.

You can script the rsync commands and run them nightly using cron.  See "man crontab" for details.

---

### Post by yuler on 2011-08-29
Will rsync image a hard drive?  I thought it only copies files.

---

### Post by SeijiSensei on 2011-08-29
> **yuler said:**
> Will rsync image a hard drive?  I thought it only copies files.

I guess I had a more liberal definition of "image" in the sense of maintaining an archive of files that could be copied back to the Windows machines once they've been restored. From re-reading the OP's request, it looks like he wants something like the kind of image dd creates so he doesn't have to deal with installing Windows if a drive fails.

The problem with your solution is that it can't be automated.  You need to manually boot from the Ubuntu CD each time you want to create a new image.  In fact, it might be easier to write these images to a large external USB drive rather than copying them over the network.

Perhaps a better solution combines both our suggestions.  Take a initial snapshot with dd like you suggest, then use rsync to mirror file changes after the snapshot is made.  To restore, you'd dd the appropriate snapshot to the new drive, boot it up, then copy over the updates using the reverse of the rsync procedure I suggested.

I'm puzzled why the OP thinks the HP OEM disk creation utility is borked, though.  I used HP's Windows utility just a couple of weeks ago to create the Win7 images that came with my daughter's HP laptop.  Wiped the disk and reinstalled from them successfully, too.  (Damn HP uses all four primary partitions, making it impossible to install Linux without re-partitioning.)

---

### Post by sbraz on 2011-08-29
to speed up the process, first you can use something like **pbzip2** which runs very good on multicore cpus as it's multithreaded, and it's 100% compatible with bzip2 classic.

also, let the best cpu do the compressing job. ;)

while you can compress the image on the source or target machine without any change to the result, if you do it on the target you'll probably hit the bandwidth limit of your network, especially if you are using a 100mbit or lower link, because 100mbit/s = 12.5MB/s... a low end 2.5" 5400 rpm drive could easily saturate the network. a gigabit link solves the problem tenfold, literally. :D

assuming that your's a private/secure network, i'd use netcat.

> I deeply resent HP/Microsoft not providing OEM disks, especially since the Windows 7 built-in utilities to create/restore images is completely borked.
honestly i'm more angry with the 5400-crappy-rpm drives big companies provide us in more or less every notebook available on the planet. i mean... in a desktop computer it's threated as OBSOLETE TECHNOLOGY, and the difference in power consumption and fault tolerance is totally acceptable.
heat would not be an issue if they engineered their laptops. yeah. i don't consider any laptop's chassis engineered at all, an 8 years old girl could do the same job with lego and some luck.

another thing is the single slot for ram on most 1gb ram netbooks, or two slots but you have two banks installed.

ultimately there's the "you MUST buy it with windows", but that's changed a bit over the years, so it's "okay".

---

### Post by u2nTu on 2011-08-30
Tried Method 1 of Yuler, and getting 'almost works' results making image of (ext3-formatted) SD card attached to router.

Data streams and zips okay (apparently), but netcat doesn't quit when done. Easy to force stop on Ubuntu side, but process is un-killable on router -- have to reboot.

Trying to open the resulting archive generates an error. Probably just needs proper termination.

Any ideas?

**EDIT:**
Using dd with 'bs' and 'count' set solves the lock-up problem, though one or the other processes must still be stopped manually (done when the file size stops changing).

Still have to try a restore of the image file to see if this really works...

---

### Post by yuler on 2011-08-31
Increase the block size to reduce the number of reads (default 512)

```
dd if=/dev/hda bs=16065 | netcat <targethost-IP> 1234
```

[http://www.softpanorama.org/Tools/dd.shtml](http://www.softpanorama.org/Tools/dd.shtml)

---

### Post by u2nTu on 2011-08-31
Thanks, yuler. Maybe the busybox version (DD-WRT on router) works a little differently. After testing several more times, found that setting the block size ('bs=') frequently causes problems.

However, just upping the count ('count=') until the default block size transferred all the data worked consistently.

Testing both ways, capture and restore, everything worked reliably. Only a few tweaks were necessary. On *writing* the archived image:
[LIST]
[*]Had to pre-write 0's to the SD card. (Tried first without; couldn't make it work.)
[*]Using merely the 'sudo' prefix (sudo bzip2...) caused permission errors. (wth?) Had to run in a root terminal -- everything then completed successfully.
[/LIST]

Also found that:

[LIST]
[*]Recording the image went reasonably fast, but writing it back was slow as Christmas. One must be patient.
[*]Doing the compression on the router was even slower! (Never again.)
[*]The target archive increases in size as work progresses, which provides some status feedback.
[*]Issuing a ^c on the PC side when done (target file size stops changing) makes a clean image. (After block transfer, netcat keeps the connection open.)
[*]As always, gparted came in handy.
[/LIST]

So for my application (as example), these were the steps:

[LIST=1]
[*]Install full busybox in router (to get 'dd' command)
[*]On PC in terminal: **netcat -l 1234 | bzip2 > routerBackup.img**
[*]On Router: **dd if=/dev/scsi/host0/bus0/target0/lun0/part1 count=1122000 | nc 192.168.1.106 1234**
[/LIST]
[INDENT]Then to write the image to SD card, in root terminal:
[/INDENT]
[LIST=1]
[*]**dd if=/dev/zero of=/dev/sdb**
[*]**bzip2 -dc ****routerBackup.img | dd of=/dev/sdb**
[/LIST]
 

> **yuler said:**
> Increase the block size to reduce the number of reads (default 512)

```
dd if=/dev/hda bs=16065 | netcat <targethost-IP> 1234
```[http://www.softpanorama.org/Tools/dd.shtml](http://www.softpanorama.org/Tools/dd.shtml)

---

