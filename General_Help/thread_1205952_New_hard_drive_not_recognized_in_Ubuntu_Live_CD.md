---
title: "New hard drive not recognized in Ubuntu Live CD"
date: 2009-07-06
forum: General Help
---

### Post by star81 on 2009-07-06
I'm using Ubuntu Live CD right now because I'm having trouble booting from my old hard drive, and I'm trying to backup all my files before doing a system recovery. So I bought a new 640GB internal hard drive today, and it showed up under Computer in Ubuntu Live CD, but when I clicked on it, it said "unable to mount location". Am I supposed to format it first before using it? And if so how do I do that?

---

### Post by lindsay7 on 2009-07-06
I would format it with Gparted as fat 32 just to get it going and then later you can do what ever you need to.  I just did this to get a new sata drive working for a home made external backup drive.

---

### Post by blueridgedog on 2009-07-06
> **star81 said:**
> Am I supposed to format it first before using it? And if so how do I do that?

Yes.  You can use the program gparted...System -> Administration -> Partition Editor.

I suggest you give some thought to how you intend to use the drive and partition it in a way that works with your plans.  

I and others here can help, but you at least need a partition of some type to mount (use).

---

### Post by star81 on 2009-07-06
Isn't the size limit for FAT32 only 4GB? Because I have a lot more than 4GB that needs to be backed up.

---

### Post by michy99 on 2009-07-06
The limit for FAT32 is 4 Gig per file, not total.

---

### Post by star81 on 2009-07-07
Thanks for the help everyone.

So I only created one partition for now and used 250GB. Will I be able to create more partitions in the future with Windows?

---

### Post by blueridgedog on 2009-07-07
Yes.  You can create four primary partition.  If you think you will need more, then make your fourth primary partition an "extended" partition, and in it you can put a number of what are called "logical" partitions.  

I generally stick to the four primary partitions.

---

### Post by Mad_Max_1412 on 2009-08-07
Guys,

I have a new 1TB drive I've installed as a second hard drive.

This will be used to store digital TV recordings on so the file sizes may be more than 4GB.

Also, I will be creating a share so I can map a drive from a WinXP box as well as see the directory from my media player.

What file system should I use?  By default the selection is Ext2.  I gather from the above postings that FAT32 won't be any good as some files are >4GB

Thanks for your advice.

---

### Post by blueridgedog on 2009-08-07
What OS's will access the drive?  If windows and Linux, then NTFS.  If only Linux, then I would go ext3.

---

### Post by Mad_Max_1412 on 2009-08-08
Hi,

NTFS isn't one of the options available.

As for what OS's will access it, it will be physically on my Ubuntu computer but I will map to the hard drive from within my WinXP computer as this is where the TV card is.  Once I trim up the TV shows, I then move them to my Ubuntu box.

Anyway, my existing hard drive is Ext3.  Should I do the new drive the same or Ext4. I just want to do it properly the first time.

Thanks

---

### Post by blueridgedog on 2009-08-08
OK, I would go with ext3 myself, but many are using ext4.

---

### Post by Mad_Max_1412 on 2009-08-08
Hi Guys,

Before doing the partition, I could go to Places --> Computer and see 3 items: My DVD player, my system disk and the new hard drive.  At this point in time I couldn't mount the new drive and my searching lead me to this thread where I found out that I had to partition it.

I've now used GParted to partition the whole of /dev/sdb as Ext3 with a name of "Media"

Now when I go back to Places --> Computer I can only see my DVD drive and my system disk (/dev/sda)

What do I need to do now?

Thanks

---

### Post by merlinus on 2009-08-08
If you wish the hdd to automount, you will have to add an entry for it in /etc/fstab.

If it is sdb1, then this should work:

/dev/sdb1 /media/sdb1 ext3 relatime 0 2

You will have to manually create the mountpoint:

```
sudo mkdir /media/sdb1
```Obviously you can change /media/sdb1 to whatever you like.

Then restart.

---

### Post by Mad_Max_1412 on 2009-08-09
Your last two words "Then Restart" made me realise that this is something I hadn't done yet, so before making any changes, I did a restart and now under "Places --> Computer" I now have 3 things:

Home Folder
File System
Media_Files (I used GParted to change the volume name from "Media" to "Media_Files")

When I right click on "Media_Files" it has an option "Unmount Volume" so it therefore must be mounted.

The only problem now is that it has a padlock symbol and the properties show the permissions being:

Owner - Root
Group - Root
Others (unspecified)

I gather I just need to change these permissions to allow me to create directories etc.

EDIT+++

I found a post in another thread where the poster started with the terminal command:

gksu gedit /etc/fstab 

The poster then said they added the following line to fstab

/dev/sdb1 /media/mynewdrive vfat user,auto,fmask=0111,dmask=0000

Since my new drive is called "Media_Files" I put

/dev/sdb1 /media/Media_Files vfat user,auto,fmask=0111,dmask=0000

I saved fstab and checked the permission and no change.

Then since GParted shows the drive as being /dev/sdb I changed the line to

/dev/sdb /media/Media_Files vfat user,auto,fmask=0111,dmask=0000

but still no changes to permissions after saving file.

I don't understand the fmask or dmask entries so it was a stab in the dark.

---

### Post by blueridgedog on 2009-08-09
First, the drive is not vfat, so the mount options you copied from your web search will not help you.

Linux native files systems are user aware and do not need a user or group argument on mount.

You appear to have it mounted at:

```
/media/Media_Files
```

So all you really need to do is change the owner of that file:
```

sudo chown USER:USER /media/Media_Files
```

(change USER to your account)

At that point you will own the mount point and will own the rood directory on the drive.

Merlinus suggested an fstab entry for you:

```
/dev/sdb1 /media/sdb1 ext3 relatime 0 2
```

Based on the mount point you just described you could use:

```
/dev/sdb1 /media/Media_Files ext3 relatime 0 2
```

Remember, you can mount media anywhere you want (I usually make a directory in my home directory for my media) and you can put shortcuts to those directories almost anywhere you want in nautilus.  Don't feel constrained by the default setup.

So taking this a step further, you can:
```

mkdir /home/USER/Media_Files (so you own it now, as you made it)
sudo umount /dev/sdb1
sudo mount /dev/sdb1 /home/USER/Media_Files
```

Then craft an entry in your /etc/fstab file to make it permanent:

```
/dev/sdb1 /home/USER/Media_Files ext3 relatime 0 2
```

Then the files will show up in your home directory...

The idea to focus on what you want and where you want your files to be.

---

### Post by Mad_Max_1412 on 2009-08-10
Thanks

I have now got it mounted at /home/max/media_files and have created 3 directories: Music, Videos, Photos

I have also gone to my Windows XP computer and managed to map a drive to media_files and I am currently copying a video file over, so it appears to work ok.

I did notice that when I mapped the drive, it did prompt me for my password so hopefully it won't need it again when I reboot the WinXP computer.

One thing I was thinking of doing once I had copied all my videos from the Ubuntu system drive to this new hard drive was to unplug the new drive (to avoid accidently over-writing it) and using a live cd of the latest Ubuntu to reformat and install a fresh copy of Ubuntu.  The reason is because I've played around a fair bit since I installed it about a year ago and whilst installing the new hard drive, I took the opportunity to remove the TV card as I never got it to work.

Anyway, I've now got my new 1TB drive installed and working (although it's a shame it really means there's only about 870Gb) so all is good.

Thanks again.

---

### Post by Mad_Max_1412 on 2009-11-02
Guys,

Please help as I think I might have stuffed something up.

Recently I purchased a Thecus N2200 NAS and I unmounted my 1TB hard drive and put it in this, thinking that my TV show files I had on there would appear on a network drive.

At the same time I downloaded the latest Ubuntu 9.10 iso and re-formatted my computer.

When I noticed that I couldn't see me files on the NAS, I took the hard drive out and put in back into my "new" Ubuntu computer.

The disk utility showed the hard drive as being /dev/sdb and it had 3 sub-components, with the 998GB one being /dev/sdb2 (see the 2 screenshots)

I therefore used a terminal and created the following directories:

sudo mkdir /media/sdb
sudo mkdir /media/sdb2

I then used the terminal to edit fstab

sudo gedit /etc/fstab

I added the following lines:

/dev/sdb        /media/sdb ext3 relatime 0 2
/dev/sdb2       /media/sdb2 ext3 relatime 0 2

I then rebooted but still can't see anything.

I then installed GParted just to see what it says and I've attached a screenshot.

What do I do now to mount my drive and confirm whether I still have my TV shows or whether I've lost them for good?

Many thanks in advance

---

### Post by dandnsmith on 2009-11-02
First off, with the drive partitioned you shouldn't be trying to mount /dev/sdb (which is the whole disk), only /dev/sdb1, /dev/sdb2, /dev/sdb3 and so on (except that there isn't any point in trying to mount your sdb1 as it is swap)

Second, your snapshots show RAID in use on the disk - I don't remember you mentioning that before when talking about partitions and format. This could be why you had trouble with it in the NAS box ...
The format for sdb2 is shown as xfs, *not* ext3

---

### Post by Mad_Max_1412 on 2009-11-02
Hi,

I've taken out the line:

/dev/sdb /media/sdb ext3 relatime 0 2

from the fstab file.

As for RAID, I have never used it.  When I installed the disk into the NAS box, I told it to set it up as JBOD (Just a Bunch of Disks)

I'm surprised the format is xfs, as you can see my posts from August when I first installed the disk that I had it set as ext3.

I've changed the other line in fstab to:

/dev/sdb2       /media/sdb2 xfs relatime 0 2

Other than a reboot, is there anything else I should do?

---

### Post by dandnsmith on 2009-11-02
That seems to cover it - if not, try checking to see if the xfs module is loaded (lsmod or modprobe?)

---

