---
title: "HELP - no GUI, huge newb with command line"
date: 2011-04-13
forum: General Help
---

### Post by onlycuteusernames on 2011-04-13
Hey, all. Complete newb here, encountering some crazy problems. I am going to try to be as detailed as possible here, because I haven't figured out my issue yet. **If you'd prefer the short version, please skip to the bottom!**

I have an MSI netbook set up with Ubuntu and the GNOME desktop enviroment. However, GNOME is currently not working at all. Starting today, and for no discernable reason, once I turn on my computer and enter my password for sda5_crypt (which is used for total system encryption), everything gets quickly ******.

Some of the time, I enter the sda5_crypt password and nothing happens at all; I just get a black screen. This is only an occasional occurrence.

Most of the time, two things come up. The Vidalia control panel, which I had set to come up on login, appears in the upper-left-hand corner of the screen; it never succeeds in connecting to the Tor network, since there is no internet. In the upper-right-hand corner, there is an error message, which reads like this:

> **Install problem!**
The configuration defaults for GNOME Power Manager have not been installed correctly.
Please contact your computer administrator.Other than those two things, there are no panels, no icons, no background picture, no menu options when I right-click in the blackness.

I have searched for ways to fix this problem on Google, but most of the quick fixes don't seem to work. I have already tried, for example:
- *sudo dpkg --configure -a *(various error messages, but "No space left on device" seems important)
- *sudo apt-get --reinstall install ubuntu-desktop* (fails to fetch anything from ca.archive.ubuntu.com)
- *sudo mkdir /var/lib/gconf/default* ("cannot create directory ... File exists")

So none of these have worked. I think one problem is that I can't connect to the internet with my computer, either through wireless or ethernet. I think that may have been the problem with reinstalling the desktop environment, since I can't get access to the Ubuntu repository. It would be REALLY HELPFUL to know how to connect to the internet through command line when I don't have a GUI at all. I haven't found out how to do this yet.

Also, if anyone knows another way to fix this problem without accessing the internet, that would be good too. I suspect that I have somehow filled up one of my important directories, such as /root.

Please bear in my mind that I mostly don't even know what I'm talking about, and some of these words I've learned in the last three hours!

---

### Post by oldos2er on 2011-04-13
"No space left on device" means your root partition is full, which is probably causing most of your problems. Can you run the commands **df -h** and **sudo fdisk -l** on your netbook, and copy and paste the output here?

Here's some info on how to free up some hard disk space: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by onlycuteusernames on 2011-04-13
This is the output for *df -h*. The underscores are just there to make it look like a table.

[FONT=Fixedsys][FONT=Courier New]> Filesystem ________________ Size ___ Used ___ Avail ___ Use% ___ Mounted on
/dev/mapper/ubuntu-root ___ 14G ____ 3.86 ___ 9.46 ____ 29% ____ /
none ______________________ 488M ___ 248K ___ 488M ____ 1% _____ /dev
none ______________________ 496M ___ 144K ___ 496M ____ 1% _____ /var/shm
none ______________________ 496M ___ 96K ____ 496M ____ 1% _____ /var/run
none ______________________ 496M ___ 0 ______ 496M ____ 0% _____ /var/lock
/dev/sda1 _________________ 106M ___ 100M ___ 1.3M ____ 99% ____ /boot
/dev/mapper/ubuntu-home ___ 95G ____ 3.6G ___ 86G _____ 5% _____ /home[/FONT][FONT=Verdana]There was too much output for *sudo -fdisk l*, filling up the screen and more. This is everything that I can see...

[/FONT][/FONT]> [FONT=Courier New]Disk /dev/dm-0: 120.0 GB, 119997984768 bytes
255 heads, 63 sectors/track, 14588 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
    
Disk /dev/dm-0 doesn't contain a valid partition table

[/FONT][FONT=Courier New]Disk /dev/dm-1: 2097 MB, 2097152000 bytes
255 heads, 63 sectors/track, 254 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
    
Disk /dev/dm-1 doesn't contain a valid partition table

[/FONT][FONT=Courier New]Disk /dev/dm-2: 15.0 GB, 14998831104 bytes
255 heads, 63 sectors/track, 1823 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
    
Disk /dev/dm-2 doesn't contain a valid partition table

[/FONT][FONT=Courier New]Disk /dev/dm-3: 102.9 GB, 102898860032 bytes
255 heads, 63 sectors/track, 12510 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
    
Disk /dev/dm-3 doesn't contain a valid partition table[/FONT][FONT=Fixedsys][FONT=Verdana][FONT=Fixedsys][FONT=Courier New]

[/FONT]  [FONT=Verdana]So I assume it's my unreasonably tiny /boot partition that's the problem? It seems I should be looking at section #6a of the link you sent me, but I'm not sure which of these methods would be best for me. I don't want to try repartitioning right now, since I don't think I'm able to back up my files. It seems that what's listed after "kernel installation failure" might make the most sense, buit I'm a little confused as to what it's telling me to do.[/FONT]
[/FONT][/FONT][/FONT]

---

### Post by SeijiSensei on 2011-04-13
> **onlycuteusernames said:**
> So I assume it's my unreasonably tiny /boot partition that's the problem? I don't want to try repartitioning right now, since I don't think I'm able to back up my files. It seems that what's listed after "kernel installation failure" might make the most sense, but I'm a little confused as to what it's telling me to do.

Yes, 100M is too small for /boot.  I usually allocate 256 or 512M for this depending on how many operating system images I'm likely to have on the machine.  What's probably happening is that the system wants to install a kernel upgrade, but there's not enough room to do so.

You don't really have many alternatives to re-partitioning.  If you want to save your files, plug in an external USB drive and boot from the Ubuntu CD.  Choose the "live" option.  You'll be running off the CD, but you'll be able to mount the filesystems on your hard drive and the USB device.  Copy what you need to save, then give gparted a try.

---

### Post by onlycuteusernames on 2011-04-13
Hmm, I've managed to delete some of the old files that were in my /boot partition, such that it is now only 47% full... And I have tried a bunch of other things, too. Nothing is working. Before I try repartitioning, I guess I'd like to know if this is definitely the problem?

Also, how would I move files from my computer onto a USB key, for example, with command line?

Thanks a lot for the help so far.

---

### Post by SeijiSensei on 2011-04-13
Easiest solution is to use rsync.  Suppose the USB drive is mounted as /media/disk.  Then:

```

cd /
sudo rsync -av home /media/disk

```

will create a copy of the entire /home structure on the USB drive.  If rsync isn't available, use "cp -a" instead of "rsync -av".

---

### Post by onlycuteusernames on 2011-04-13
If I only wanted to copy certain files, though, how could I do that? I don't have the space to copy all the files on my computer, especially my music, which I have backed up elsewhere anyway. More important is documents and some images. Even if I was going to copy it all to one place, I would need to do that in loads... I have only a 2gig USB key available right now.

---

### Post by SeijiSensei on 2011-04-14
Use the cp command.  Type "man cp" at the terminal prompt for details.

---

