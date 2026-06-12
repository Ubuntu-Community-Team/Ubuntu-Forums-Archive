---
title: "new external hard drive missing space"
date: 2010-02-05
forum: General Help
---

### Post by mlwalla on 2010-02-05
Saw a good deal on an a 1TB HP SimpleSave external usb hard drive, so I bought it.  The hard drive came formatted NTFS with some back up software that's windows only, so the first thing I did was delete the only visible partition and reformat the drive to a single ext3 partition using gparted.  

But when I mount the drive, there's only 869gb available, and gparted says some 48 gig are being used.

Also, when I plug the drive in, ubuntu is still mounting an empty iso called HPLauncher at /media/HPLAUNCHER and I can't see why it would do that when I deleted everything on the drive already.

Any ideas to get back the missing space and get rid of the ghost iso (besides manually unmounting)?

Thanks a mint, community.

---

### Post by tom.swartz07 on 2010-02-05
> **mlwalla said:**
> Saw a good deal on an a 1TB HP SimpleSave external usb hard drive, so I bought it.  The hard drive came formatted NTFS with some back up software that's windows only, so the first thing I did was delete the only visible partition and reformat the drive to a single ext3 partition using gparted.  

But when I mount the drive, there's only 869gb available, and gparted says 14.8 gig are being used.  Any ideas?

Also, when I plug the drive in, ubuntu is still mounting an empty iso called HPLauncher at /media/HPLAUNCHER and I can't see why it would do that when I deleted everything on the drive already.

Any ideas to get back the missing space and get rid of the ghost iso (besides manually unmounting)?

Thanks a mint, community.

Heres what I would do:

Plug the drive in, then manually 'unmount' it from the computer- just leave it plugged in.

Fire up gParted, and navigate to the new drive. Wipe the entire partition table off of it completely, and re-format it again.

If you specifically delete the partition table, when gParted goes to create a new format to it, you will reset all of the filesystem info on the drive. 

That should take care of it!


PS- What OS are you on? 9.04, 9.10, or something else?

---

### Post by SecretCode on 2010-02-05
Firstly, a 1TB drive is 1,000,000,000,000 bytes which is only 931GiB (or something).

Secondly, ext3/ext4 will require space for the journal, even on an empty drive.

Thirdly, ext3/ext4 will by default reserve about 5% for root use in special situations. This part you can do something about - look at **tune2fs**. For a data-only drive it's not so important and for modern large drives 5% is way too much.

Even with all that said, there must be something on there to give this HPLAUNCHER. The previous recommendation should sort that out.

---

### Post by Ordes on 2010-02-05
> Secrect Code pretty much said it all;

and 1Tb drive will never be 1Tb in a PC system. The 1TB written on it is in metric system >> 1,000,000,000,000 bytes

In binaric (the system a pc uses) it doesnt work like this, 1024 bytes are 1 Kb, 1024 Kb are 1 MB and so, so you will gradually loose capacity.

Its always around ~7% +-

> 1tb > 1000gb =~ 70gb (7%)

---

### Post by mlwalla on 2010-02-06
> Heres what I would do:

Plug the drive in, then manually 'unmount' it from the computer- just leave it plugged in.

Fire up gParted, and navigate to the new drive. Wipe the entire partition table off of it completely, and re-format it again.

If you specifically delete the partition table, when gParted goes to create a new format to it, you will reset all of the filesystem info on the drive.


How is this different than what I did before?  I don't see an option for 'delete entire partition table' other than just 'delete partition' which is what I did the first time through before making a single ext3 partition...

---

### Post by tom.swartz07 on 2010-02-06
> **mlwalla said:**
> How is this different than what I did before?  I don't see an option for 'delete entire partition table' other than just 'delete partition' which is what I did the first time through before making a single ext3 partition...

When you wipe the partition table and create a new one, all of the previous file location data is lost entirely. Rather than formatting, which simply gives the drive a new file structure, possibly leaving any files previously on the drive there.

---

### Post by mlwalla on 2010-02-06
Ok I tried 'Create New Partition Table' under the 'Device' menu in Gparted left it at the default type 'msdos' and then created one partition on the drive again, ext3.

Same thing as before.  In nautilus, only 869.5gb free and some 46gb used...which I guess is the 5% reserved for root by ext3?  Haven't tried tune2fs, but will likely try to pare that down as 46 gb is larger than the internal drive in my usf desktop.

But I'm still getting HPLauncher.  I wonder if that's somewhere else in the box for the external drive?  Weird stuff. Anyone else used this drive before?  HP SimpleSave 1TB

I'm running karmic from an upgrade, but I'll be doing a fresh install for lucid methinks.

---

### Post by tom.swartz07 on 2010-02-06
> **mlwalla said:**
> Ok I tried 'Create New Partition Table' under the 'Device' menu in Gparted left it at the default type 'msdos' and then created one partition on the drive again, ext3.

Same thing as before.  In nautilus, only 869.5gb free and some 46gb used...which I guess is the 5% reserved for root by ext3?  Haven't tried tune2fs, but will likely try to pare that down as 46 gb is larger than the internal drive in my usf desktop.

But I'm still getting HPLauncher.  I wonder if that's somewhere else in the box for the external drive?  Weird stuff. Anyone else used this drive before?  HP SimpleSave 1TB

I'm running karmic from an upgrade, but I'll be doing a fresh install for lucid methinks.

Did you try examining the contents of HPLauncher? See if you could access it and figure out what it is?

---

### Post by mlwalla on 2010-02-06
Well nautilus and Disk Utility think it's a cd, but there doesn't appear to be anything on it.  I don't currently have an optical drive.

---

### Post by Paul Hugill on 2010-03-06
Hi Guys,
Secret code, you mentioned that the 5% reserved space on a data only drive is too much, what is a reasonable amount to change it to?

I've read some stuff saying dont change it to 0 but nothing to suggest what it can be.
I can live with losing the 16GB for the journal compared to NTFS but to lose another 45GB on a drive that just sits there with relatively static data is a bit too much. 

I'm using Karmic and the drive is formatted as ext4 but is not used for the system partition or anything.

Thanks for the help, I'm pretty new to Linux so was a bit shocked to see how much space I lost on it compared to Windows. If there is a better format to use on a storage drive that would be good to know.

Thanks,
Paul

---

### Post by 98cwitr on 2010-03-06
you could just format it into FAT32 right?

---

### Post by Paul Hugill on 2010-03-06
Except that FAT32 doesnt let you have files bigger than 4GB or any security on them.

I need something that gives the same features as NTFS/EXT4 with the max amount of space (I'll live with the space lost for the journal as I can see the point of that).

Paul

---

### Post by SecretCode on 2010-03-07
> **Paul Hugill said:**
> Hi Guys,
Secret code, you mentioned that the 5% reserved space on a data only drive is too much, what is a reasonable amount to change it to?

I've read some stuff saying dont change it to 0 but nothing to suggest what it can be.


Hmm. I haven't read any such stuff. But I don't claim any expertise ... it may be worth searching for posts mentioning **tune2fs** and **ext4**.

---

### Post by simosx on 2010-06-15
> **mlwalla said:**
> Well nautilus and Disk Utility think it's a cd, but there doesn't appear to be anything on it.  I don't currently have an optical drive.

That's a virtual device that makes sense for Window users.
In Ubuntu you can use usb-modeswitch, [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)
in order to disable it from appearing. usb-modeswitch needs to be configured with the details of your device so that when you connect it, that CD will not appear. Search this forum for a discussion on usb-modeswitch and the parameters of this disk.

---

