---
title: "mount: unknown filesystem type 'jbd'"
date: 2009-11-15
forum: General Help
---

### Post by rchr on 2009-11-15
Hello.  I'm on up-to-date Ubuntu Karmic Since yesterday something weird happend to my external HDD.  I'm using Truecrypt to encrypt/mount this drive and all of a sudden it started giving me this message while mounting > mount: unknown filesystem type 'jbd'  There was one ext3 partition on this HDD, created with Truecrypt using it's wizard and was mounting/working without any problems until yesterday.  HDD is pretty new (~3-4 weeks), there was no power failures or anything that could physically damage the drive.  While it happend I wasn't writing any data on the disc, I had one video clip from this drive opened with VLC (on pause for about an hour), then I tried accessing some catalogs with Nautilus but it didn't read anything, I tried unmounting partition but it gave me an error that it's still in use so I remembered about VLC, which didn't want to unpause this clip and didn't want to close itself either so I forced the it's close with system monitor and then partition unmounted, I unplugged the drive and plugged again and after that it didn't mount again... I have no idea if it's related to this file opened with VLC but I don't remember doing anything else with the drive.  Please help... I have no idea what to do now, I'm just a casual user and don't want to do anything that might destroy data on the drive. Is there anything I can do to fix this or gather more imformations about the issue without damaging the partition? Maybe fsck or commands described at [http://masutu.livejournal.com/](http://masutu.livejournal.com/) ? But how to do all this with partition that is truecrypt'ed...  and most important, is it safe

---

### Post by rchr on 2009-11-16
I've read lots of faqs about repairing ext3 and found out that the issue was cause by damaged "superblock" and managed to come up with simple solution :) so here it is if anybody encounter such issue: open drive with following command > truecrypt -t --filesystem=none /dev/{YOUR_DRIVE} use following to check for sectors with "superblock" backups > mke2fs -n /dev/mapper/truecrypt1 in my example first backup was at 32768, so the next command restores this backup > e2fsck -b 32768 /dev/mapper/truecrypt1 in my case it took about 2 hours to scan the drive and needed few thousands (!!) confirmations on "Fix(y)?" but it fixed the issue and restored everything dammit :) hope it helps somebody

---

### Post by Petra Roosen on 2012-10-06
> **rchr said:**
> hope it helps somebody

It definitely did! ):P
I happened to need some files from a LUKS encrypted backup disc, and a faulty USB controller seems to have shreddered my files while processing.

Your suggestion helped repairing the fs again!

Thanks a lot!

Petra

---

