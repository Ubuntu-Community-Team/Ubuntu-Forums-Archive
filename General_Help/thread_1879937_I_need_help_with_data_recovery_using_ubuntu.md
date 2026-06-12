---
title: "I need help with data recovery using ubuntu"
date: 2011-11-12
forum: General Help
---

### Post by Kuromeshi on 2011-11-12
Hi, i'm pretty new to the ubuntu os, as i'm mainly a windows user. Recently, I had a major hard drive failure with 64 bit windows 7. I could not normally access the drive because of the fact that I had major booting errors and I could not get past start up. I recently was using the latest build of ubuntu (booting it all from disk) to try and get to my file system and it worked just fine and i could access my drive for a shot period of time, before my laptop with the effected hard drive's power supply came unplugged while i was rebooting ubuntu and it did not shut down properly. My issue is, I can still boot up ubuntu and try to force mount the drive, however i get an input output error in the console when I try to mount it. It tells me to run /f chkdsk, but since I cannot get to windows I have no idea how I can. I tried to use ntfstools to fix the problem but it did not work. I really don't want to have to mess around with this too much or take it to some place that will charge me $1000+ for data recovery when i'm sure there is a simpler way to do it using ubuntu. Please help me guys, any responses would be appreciated from you fine folk! :(
 
Other information:
My laptop's hard drive is formatted into 3 partitions; sda1, sda2, and sda3. sda3 seems to be the one effected drive as it's the one with all my previous files on it, the other two are system partitions.
I am using a stock dell 1545 laptop normally running windows 7 64 bit
I have tried both the newest and last stable/supported release of ubuntu on this and right now i can only use the last stable one to even see the drive, the latest doesn't have it show up anymore. (It turned off during shut down while i was using the latest release, so then I tried the previous to see if I could locate the drive with the last stable.)
 
I originally tried to follow this guide: [http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)
And this one for the mounting I/O error: [http://ubuntuforums.org/showthread.php?t=1144175](http://ubuntuforums.org/showthread.php?t=1144175)
 
 
Also, i'm not afraid to admit i'm more on the end user side of things, so any answers or solutions will have to be spelled out as simple as possible for me. Sorry! >_<

---

### Post by carranty on 2011-11-12
Can you please paste the command your using to try and mount the drive, as well as the error message.  

Also, just to be clear.  Your laptop's hard drive (or rather the sda3 partition) is the issue and you've successfully booted the laptop into Ubuntu using the live CD.  All you want to do is mount the drive so you can backup your files before doing a fresh install.  Is that right?

Thanks

---

### Post by dragonfly41 on 2011-11-12
I've had problems before with Windows crashes and so some time ago I created a dual boot (Vista and ubuntu 10.10) on separate partitions.   For good measure I have a second copy of ubuntu on external USB drive.

I still have to use some windows apps so I'm replying to this from windows Vista.

I had a startup problem recently on windows (Vista). Windows would login and startup but not get as far as the desktop showing. Lots of activity on the disk LED.

I rebooted into ubuntu and inspected the windows partition with ubuntu disk utility and this alerted me to bad sectors in the windows partition.

It was cured by starting up windows in safe mode + command prompt.
Then at command prompt run chkdisk c:/r (assuming that your windows volume is c:).   Then reboot into windows normal mode (not safe mode).

You have to leave the diagnostics running to completion .. perhaps several hours.   chkdsk has five tests to go through.

So provided that you can startup in windows safe mode (you write that you could not get past start up .. but can you get into safe mode?) I would try this first before considering data recovery through ubuntu.

---

### Post by Kuromeshi on 2011-11-12
> **dragonfly41 said:**
> So provided that you can startup in windows safe mode (you write that you could not get past start up .. but can you get into safe mode?) I would try this first before considering data recovery through ubuntu.
 
 
Well, I used to be able to get into safe mode, but I can no longer do so in order to run chkdsk the only options i can do that I know of are f2 for setup and f12 for booting from another device :/


> **carranty said:**
> Can you please paste the command your using to try and mount the drive, as well as the error message. 
 
Also, just to be clear. Your laptop's hard drive (or rather the sda3 partition) is the issue and you've successfully booted the laptop into Ubuntu using the live CD. All you want to do is mount the drive so you can backup your files before doing a fresh install. Is that right?
 
Thanks

Also, yes that is what i want to do. I need to be able to backup my hard drives files so i can wipe it and do a fresh install. I will try and have the commands i've used to you in a minute, as soon as ubuntu finishes booting from disk.

---

### Post by Kuromeshi on 2011-11-12
Ok, the first thing I did when I opened up ubuntu is I went to places > computer > and tried to double click on "320 GB Hard Disk OS" It said it was opening it, however it stopped and gave me this error message: "Unable to Mount Location: Dbus error org.freedesktop.DBus.Error.NoReply: Did not recieve a reply. Possible causes include: the remote application did not send a reply, the reply timeout expired, or the network connection was broken."
 
At this point, I opened up a terminal to try and force mount the drive
 
First I used: sudo /bin/bash
Then I used: mkdir /media/disk
Then: mount -t ntfs-3g /dev/sda3 /media/disk -o force
 
Then I got this message in the terminal:
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read vcn 0x3: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g./dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details.
 
At this point I close that terminal and open a new one.
 
First I use: Sudo apt-get install ntfsprogs
then: sudo ntfsfix /dev/sda3
 
Then I get 
Mounting volume... pread: Input/output error
Failed to calculate umber of free clusters: Input/output error.
FAILED
Attempting to correct errors...
Processing $MFT and $MFTMirr...
Reading$MFT... OK
Reading $MFTMirr... OK 
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)...
pread: Input/output error
Failed to calculate number of free clusters: Input/output error.
Remount failed: Input/output error.
 
 
I don't know what to do from here since ntfsfix can't fix the error with mounting the drive and I can't even forcemount it :/

---

### Post by dragonfly41 on 2011-11-12
Here is another shot ..

When in ubuntu download the Windows 7 recovery disk

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Burn *.iso to CD using brassero.

Boot up recovery CD (you will need to choose CD bootup in F12).

Try the recovery options.

---

### Post by Kuromeshi on 2011-11-12
> **dragonfly41 said:**
> Here is another shot ..
 
When in ubuntu download the Windows 7 recovery disk
 
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
 
Burn *.iso to CD using brassero.
 
Boot up recovery CD (you will need to choose CD bootup in F12).
 
Try the recovery options.
 
Do you have a link to a free download of it?

---

### Post by carranty on 2011-11-12
I'm sorry, I don't think I can be of help on this :confused:.

---

### Post by dragonfly41 on 2011-11-12
I think these are free ..

[http://www.proposedsolution.com/downloads/download-windows-7-vista-bootable-disc-cd-dvd-iso-image/](http://www.proposedsolution.com/downloads/download-windows-7-vista-bootable-disc-cd-dvd-iso-image/)

---

### Post by Mark Phelps on 2011-11-12
Sorry to tell you this ... but ... the only time CHKDSK will take HOURS on a disk is if the disk is in the process of failing.  It's taking so long because every time the utility hits a possibly bad sector, it tried to read it over and over, until it times out.  With a failing disk, this can happen hundreds of times.

The disk images are Repair CDs -- which can only be used to repair a damaged Win7 boot loader.  Fortunately, the loaders are the same for Vista and Win7, so you can use a Win7 disk to do the repairs.  Actually, the Win7 disk works better on Vista than does the Vista disk.

If that is all that was wrong, chkdsk would have taken a few minutes at most to run.

So, maybe you'll be lucky and that will fix it enough to get Vista loading again -- but I doubt that will happen.

In that case, you need consider hooking up the drive to a Windows PC to do data recovery.  In general, I have found that Windows utilities do the best job of recoverying data from Windows partitions; Linux utilities do the best job of recovering data from Linux filesystems.

The best Windows data recovery tool I've used is GetDataBack from Runtime Software.  You can download the trial, install it, and run it for free.  But you will need to install it on a Windows PC, hook up your drive to that PC, and let it run overnight.  Then, in the morning, check it to see what it found.  IF it found the files you want to save, then go online, purchase the software, apply the activation code, and do the file recovery -- to another disk.

Your data -- your money -- your decision.

---

### Post by Cyclane on 2011-11-12
Have you tried recovering the partition to a file?

[https://help.ubuntu.com/community/DataRecovery#Imaging_a_damaged_device.2C_filesystem_or_drive:](https://help.ubuntu.com/community/DataRecovery#Imaging_a_damaged_device.2C_filesystem_or_drive:)
> First you copy as much data as possible, without retrying or splitting sectors:

ddrescue --no-split /dev/hda1 imagefile logfile 
Now let it retry previous errors 3 times, using uncached reads:

ddrescue --direct --max-retries=3 /dev/hda1 imagefile logfile 
If that fails you can try again but retrimmed, so it tries to reread full sectors:

ddrescue --direct --retrim --max-retries=3 /dev/hda1 imagefile logfile 

I recommend plugging in a USB disk. I believe the disk has to be somewhat bigger than the partition you're recovering (I don't know how much) After that you can copy it back to another device/partition or mount the imagefile on a linux machine.

---

