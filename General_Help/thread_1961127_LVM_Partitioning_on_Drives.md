---
title: "LVM Partitioning on Drives"
date: 2012-04-18
forum: General Help
---

### Post by Wickd on 2012-04-18
Hi All

I need some advise with regards to the setup of LVM on my Ubuntu Server machine.

I currently have 3 drives in place:

1) 250 GB drive (3 partitions) --> For Ubuntu installation
2) 1 TB drive (1 NTFS partition) --> For Media (Currently full)
3) 1 TB drive (1 NTFS partition) --> For Media (Currently Empty)

I currently have 3 samba shares for Music, Video and Applications on the 2'nd drive. So instead of setting up another 3 shares on the empty drive (no 3), I would like to set a LVM to combine 2 and 3 into 1 Logical Volume for my media.

I have a couple of questions regarding this.

1) Do I have to reformat 2 and 3 to LINUX LVM?
2) If I do this and use both drives, and one fails, do I lose all data?
3) Is there any other alternative that could accomplish this task

Any Ideas with regards to this, will be much appreciated :)

Thanks

---

### Post by 1clue on 2012-04-18
1.  Yes, but it can be done one at a time.
    a.  Set up disk 3 as lvm and format it.
    b.  Make your partitions as you want, with room to hold the data from disk 2.
    c.  Set up disk 2 as lvm and format it.
    d.  Grow the filesystems you created as appropriate.
2.  Yes.
3.  You could combine RAID and LVM, where the RAID has some sort of redundancy.

---

### Post by 1clue on 2012-04-18
Sorry but I left out a few critical items.

Between b and c, you would want to mount all the volumes and copy your data over.

And regarding alternate solutions, you could get a removable jumbo drive and every day|week|month|whatever you drag a copy of everything you need to keep onto it.

Personally I use 4 identical disks with lvm but not RAID for my runtime installation.  I also have a slot on the front of my machine that takes a raw sata drive as though it were a tape cartridge.  I stick a drive in the slot, drag the backup onto the extra drive, eject it and that's it.  The drive sits on the desk and so anything short of a direct lightning strike or fire will be harmless.  A really good strategy would cycle between 2 or 3 of these drives, and at least one would be off-site at all times.  The thing is though, the really critical thing I have is my address book, my email history, my music and my pictures.  All that stuff is on my phone too, so it goes with me wherever I go.

I started using backups back in the 1980's.  I've gone through a lot of different strategies, including floppies, tapes, CDs, network drives, DVDs, BD-R, RAID, RAID+LVM and just about anything else, and right now I just drag a few folders over every week.

IMO unless you're just learning about something and want to try it, you should consider what it is that you want to accomplish and then consider every solution you can come up with.  For me, personally, I'm more interested in speed than in reliability.  Not much (data) on the system isn't somewhere else too, so if lightning strikes chances are some part of it will survive.

---

