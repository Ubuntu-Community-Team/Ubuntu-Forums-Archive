---
title: "Partially dd'd my hard drive, need to get data back from non-dd'd part"
date: 2011-04-12
forum: General Help
---

### Post by WatsonDE on 2011-04-12
Well this is one for the "note to self" archives - don't type "sda" when you mean "hda"...

I decided today that I was finally going to reinstall Ubuntu and BackTrack onto encrypted partitions with pre-boot authentication.  Before this choice, I had a partition for the main Ubuntu files, a Ubuntu home partition, a Ubuntu swap partition, a BT partition, a small boot partition, a Windows partition, and a partition I used for storage for all 3 OS's.  None of these partitions are encrypted, except the /home folder uses the standard "make your home folder private" option chosen during the Ubuntu install.

I've already backed up my important BT and Windows files but I hadn't done my Ubuntu ones.  So I backed up my important files from my /home folder and elsewhere onto a USB stick, then booted up from a BT live CD (have to install BT first).  Started up dd if=/dev/urandom of=/dev/hda (in BT my hard drive is hda) and it was going slow as a slug and had no progress bar; so after 150mb or so I killed it and installed *clpbar *(command line progress bar, a great little tool) so I could know how far along dd was.  I had my USB disk plugged in because there were a few files I needed for the BT install.  When I restarted dd I accidentally typed of=/dev/*sda *instead of of=/dev/*hda*.  I caught the error but by the time I did it had already wiped about 40mb off the beginning of my USB stick, including a good chunk of the files in the (inconveniently-named) folder "backup" which contained, among other things, small .odt and txt files, as well as the partition tables and whatever else is in the first few mb.

I tried using testdisk to recover the partition info from my hard drive and USB drive, but it couldn't pick the partitions up.  I imaged the USB key and used *foremost* to recover a lot of files from there even though the partition table had been wiped out, but obviously couldn't get the part that'd been dd'd with /dev/urandom.  My /home partition didn't start until about 10GB into the drive, so I don't think it got DD'd with the initial 150mb, so if I can find that spot on the disk all my files should be fine and I should be able to recover them.  My problems are this:

     1.  *foremost* only picks up certain file types, and not all of the files I'm trying to recover are listed.  For some reason, it seems to pick up files which are actually .odt files as .sx files for some reason, which works with a little copy/pasting, but other files it won't pick up at all even though I know they're there (this is based off my USB drive experience);

     2.  My /home folder uses the standard Ubuntu "during install you can make your home folder private" encryption (I have the key it gives you when you set it up and my passcode), so I don't know what to tell *foremost* or any other tool to look for in the image, and with a 80gb drive image there's going to be LOTS of files to go through.  Also, if it doesn't pick up the filetype of the encrypted /home, it's not going to be very helpful;

     3.  I don't know how to mount the encrypted /home partition either without recovering it or directly mounting it.  I've read through a few of the tutorials but they've not been very helpful when I don't even know where to find the /home partition in the drive image.

     Any help would be greatly appreciated.

---

