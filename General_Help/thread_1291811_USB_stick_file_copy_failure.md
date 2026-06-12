---
title: "USB stick file copy failure"
date: 2009-10-15
forum: General Help
---

### Post by StuartN on 2009-10-15
I am copying files of a few GB (but less than 4 GB) to a brand-new 8 GB memory stick. This stick works without problems on my desktop but on my laptop I am getting a failure to copy large files. At some point the drive simply unmounts and the copy dialog returns an IO error. In dmesg I get:

```
reset high speed USB device using ehci_hcd and address 2
```

Is there anything I can change on my laptop to make this more reliable?

---

### Post by zer0x on 2009-10-15
Hi,

That sounds pretty strange! Could you test the usb stick for Input/Output errors on both machines using dd? Backup anything you need from the usb stick, and make sure it is not mounted. Just a reminder, this will entirely wipe the usb stick!

```
sudo dd if=/dev/zero of=/dev/sd(?) bs=1M
```

Replacing (?) (and remove brackets) with the appropriate letter.

**Be _very_ careful with that command though! Triple check your pointing at the correct block device as it will fill it with zeros!**

To verify you have the correct block device check the output of

```
sudo fdisk -l
```

If you are at all unsure, post back here!

To get the usb stick back to normal, you'll need to repartition it (e.g. fdisk), and reformat it (e.g. mkfs.vfat -F32)

zer0x

---

### Post by P4man on 2009-10-15
Ive never seen it myself, but from reading around it seems linux is a bit more picky about USB than windows.  you could try this:

```
sudo modprobe -r ehci-hcd
```

It will unload USB 2.0 driver, giving you only USB 1.1 speeds, but it might help until you find a better solution.

---

### Post by StuartN on 2009-10-15
Okay, this is a new one on me - I bought this 8 GB stick on special offer. I just stuck it in a Windows machine and it is (don't laugh, I double-checked) a 500 MB SCSI CD-ROM containing Pelican U3 Launchpad and a 7.5 GB FAT32 data partition. I only want the data partition, but have not seen a way to erase this pretend CD-ROM.

So

1) Gparted seems ignorant of the partition pretending to be a CD-ROM, and

2) the Ubuntu 8.10 desktop handles the data partition fine at 40-50 MB/s, while the Ubuntu 8.04 laptop is a crapulent 1-2 MB/s and fails on about half of all file copying.

---

### Post by zer0x on 2009-10-15
Hi,

If you follow the above instructions on zeroing out the usb stick, then re-partition and format it, your problem should be resolved :D

Trying not to sound like a stuck record, be very careful with the dd command, and post back here if you are unsure about anything!

I'd double check the output of 'mount', to see if more than one partition on the usb stick is mounted, and then make sure to unmount them all before zeroing out the usb stick.

zer0x

---

### Post by StuartN on 2009-10-15
> **zer0x said:**
> If you follow the above instructions on zeroing out the usb stick, then re-partition and format it, your problem should be resolved

I am just doing that now.

After seeing the Pelican U3 CD-ROM pop up in Windows I searched and found the comment below, but I prefer your method. Hopefully I will be the happy owner of the plain 8GB stick I thought I bought.

"Go to [http://www.U3.com](http://www.U3.com) for support. I didn't even bother with uninstalling NERO to test their theory. I went to: [http://www.u3.com/uninstall/](http://www.u3.com/uninstall/) then downloaded and ran the U3 uninstall exe (on a pc that worked with the U3 Cruzer). Now I have a single 1GB drive instead of a 6MB CD and <1GB drive. Sure the U3 promises a lot of great things, but I needed a USB key that works on any PC, not a portable user preferences/email documents folder. I am much happier now :)" [http://ubuntuforums.org/archive/index.php/t-207683.html](http://ubuntuforums.org/archive/index.php/t-207683.html)

---

### Post by StuartN on 2009-10-15
**zer0x**, Just to calm the kittens, this is meant to take about an hour, right?

(No progress indication, 8,000 MB at 2 MB/s -> 67 minutes)

---

### Post by zer0x on 2009-10-15
Yep, don't worry it'll get there in less than an hour :D (I should have said in around an hour, 2MB/s is below average for writing to a usb stick, but usb stick read/write speeds vary dramatically, no output is normal, it will give you a summary when its complete).

Wiping the entire usb stick like this will act as a check for I/O errors also!

---

### Post by StuartN on 2009-10-15
> **zer0x said:**
> Wiping the entire usb stick like this will act as a check for I/O errors also!

Okay, it ended up empty at 7.48 GiB. I am copying a big file (at 3 MB/s) and haven't seen an error yet.

BUT, isn't 500 MB still missing? And dmesg is showing errors on a phanton CD-ROM:

```
[ 5654.836285] sr 8:0:0:1: [sr1] Sense Key : No Sense [current] 
[ 5654.836293] sr 8:0:0:1: [sr1] Add. Sense: No additional sense information
[ 5654.836303] end_request: I/O error, dev sr1, sector 196600
[ 5654.837652] sr 8:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
```

So it seems this stupid Pelican U3 thing is still hanging in there and I'll have to nuke it on a Windows machine. What kind of a&#1071;shole would put a phantom CD-ROM on a class-compliant USB device and have it intercept all saves, without even appearing (or having the option to uninstall) in any OS but Windows? They could have just put an install .exe on the stick for people who did want it.

---

### Post by P4man on 2009-10-15
I had something similar on a sandisk cruzer. It would have a second "partition" (which wasnrt really one). The only way to remove it was using a tool from sandisk which was windows only.

If yours also has this U3 thing, have a look here:

[http://u3.com/support/default.aspx#CQ3](http://u3.com/support/default.aspx#CQ3)

---

### Post by StuartN on 2009-10-15
Thanks for all the help.

I have stuck this thing in a Windows machine, extracted the zipped removal tool and nuked the U3 partition. It is like the Galactic HyperPass plans available for public inspection in the unlit basement, guarded by a leopard.

So it is now formatted to 7.5 GiB (which I think is 8 GB) and transferring away at 6 MB/s on the laptop. The dektop was much, much faster and seemed completely untroubled by the U3 stuff, which might be that it is Ubuntu 9.04 rather than 8.10.

Anyways, now I can carry on with the grand project - ripping film to hard disk. The oldest are hand-cranked, variable frame rate movies. The newest are S-VHS. The film went through a tele-cine to VHS conversion, then everything went VHS to DVDR. This last step from DVDR to hard disk is the quickest and easiest, and there is no fear of the films disintegrating during playback! I am doing it on a laptop because there are builders at work here and the power goes off randomly, so this is the closest I have to a UPS.

---

### Post by zer0x on 2009-10-15
That is unpleasant :/ Looks like you will have to use that U3 uninstaller in Windows, which I assume re-flashes the sticks firmware..

I would re-run the dd wipe once you've got that done to double check the stick is clean and has no errors.

zer0x

Oops, missed your last post, 6MB/s is much better :D Glad its sorted!

---

### Post by StuartN on 2009-10-15
> **zer0x said:**
> Oops, missed your last post, 6MB/s is much better :D Glad its sorted!

Yes it is sorted, thanks so much. My desktop is handling the USB stick at 25 MB/s though, but I guess that is just the laptop hardware restricting it to 6 MB/s.

I've done a baptism, a first holy communion, a wedding and a television interview since getting this big stick working. There is shelf loads of this stuff all migrating onto hard disk, and so much free space. I had already done all my CDs, audio tapes and DVDs. By some kind of magic they are all neatly catalogued and can be played anywhere.

---

### Post by zer0x on 2009-10-15
> **StuartN said:**
> Yes it is sorted, thanks so much. My desktop is handling the USB stick at 25 MB/s though, but I guess that is just the laptop hardware restricting it to 6 MB/s.

I've done a baptism, a first holy communion, a wedding and a television interview since getting this big stick working. There is shelf loads of this stuff all migrating onto hard disk, and so much free space. I had already done all my CDs, audio tapes and DVDs. By some kind of magic they are all neatly catalogued and can be played anywhere.

Excellent! I'd assume the same now you know this stick is 'normal' :D

That sounds like a lot of work! Did you see the link I posted last night for DVD -> XviD transcoding?

[http://ubuntuforums.org/showthread.php?t=1289964&page=2]("http://ubuntuforums.org/showthread.php?t=1289964&page=2")

I am really impressed with it! Very clear, and covers the basics of some very useful features! 

Cheers,

zer0x

---

### Post by StuartN on 2009-10-15
> **zer0x said:**
> Did you see the link I posted last night for DVD -> XviD transcoding?

I did, and I must answer it in that thread - mencoder bombs out, AviDemux bombs out, nothing seems to work on those files. They are .VOB files from dual-layer DVDs and it doesn't matter whether I rip into one single .VOB bigger than 4.2 GB or several 1 GB .VOBs, I cannot get a decent edit of the video after the 4.2 GB point. The .VOBs actually play fine, which is okay for films, but I can't split a series into episodes.

I will rerun mencoder and run Avidemux in a terminal and post the errors if you are interested.

To be honest the personal stuff, which is all on single-layer DVD, is ripping absolutely fine and I am not too concerned with putting the commercial DVDs on hard disk unless it is easy.

---

### Post by zer0x on 2009-10-15
Always Interested :)

I'll keep an eye on the original thread!

---

