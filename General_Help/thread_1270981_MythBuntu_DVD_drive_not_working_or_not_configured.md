---
title: "MythBuntu: DVD drive not working or not configured ?"
date: 2009-09-20
forum: General Help
---

### Post by Raptor Ramjet on 2009-09-20
Hello,

I have a MythTV system where the DVD Drive is not working.  When I boot from a CD it is recognised and I can run various live CDs etc. so this is definitely not a hardware issue.

However in MythTV I pop a shop bought DVD in the drive, wait for it to spin up, then press the "Play DVD" menu.  The screen briefly blanks out but nothing else happens.  So I try a different DVD.  Same result.  At this point I take the DVDs over to my windows machine where they both play perfectly first time. Ho hum, time to go to the command line....

A short while later and I can see that my fstab entry for the device has been set up at installation time as:

```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

I then tried using VLC with "media" > "open disk" supplying values of "/dev/dvd" (which was set up as the default), "/dev/cdrom", "dev/cdrom0", "/media/cdrom" and "/media/cdrom0".

In all cases I get the same error message of "Your input could not be opened" and nothing happens.  

Using Thunar I then attempt to view the four locations mentioned above and none of them contain files so I can only assume the DVD is either not being mounted, is being mounted somewhere else or the system is screwed up

If anyone could therefore tell me how Ubuntu sets up and uses DVD drives I would be most grateful as compared to Windows "good old" drive letters this is like having teeth pulled with no anaesthetic whilst being repeatedly stung in the genitals by wasps.

<rant>
In fact I can safely say that trying to set up a MythTV box has been the single worst, most frustrating time sink I have ever encountered.  

I'm getting so fed up with it I'm seriously considering wasting a huge pile of money by shelling out for Windows Media Centre as having initially done a test build with Windows (to check the hardware was all working) at least with Windows I can watch TV, play DVDs, the remote works etc. etc. without me having to spend hour, after hour, after hour,  after hour scrabbling about on google, trawling forums, hand tweaking config files etc. etc.
</rant>

---

### Post by Raptor Ramjet on 2009-09-22
Well after more frustrating hours googling I've now found that there does appear to be a DVD detected as the output of dmesg gives me the following:

```

me@pc:~$ dmesg | grep DVD
[    8.128069] ata3.00: ATAPI: PIONEER DVD-RW  DVRTD08, 1.09, max UDMA/33

```

However there appear to be no symlinks for the device in "/dev" as there are no entries for "/dev/dvd", "dev/cdrom" or even "/dev/scd0" (or anything else that looks like a DVD writer device).

Having done some more research I'e also found some stuff output from dmesg that looks relevant:

```

me@pc:~$ dmesg | grep ata3
[    1.427522] ata3: SATA max UDMA/133 abar m8192@0xfce76000 port 0xfce76200 irq 2301
[    2.724014] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    7.736015] ata3.00: qc timeout (cmd 0xef)
[    7.736018] ata3.00: failed to enable ATAPI AN (err_mask=0x4)
[    7.736071] ata3.00: ATAPI: PIONEER DVD-RW  DVRTD08, 1.09, max UDMA/33
[    7.736086] ata3.00: failed to set xfermode (err_mask=0x40)
[    8.220014] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   18.232013] ata3.00: qc timeout (cmd 0xef)
[   18.232016] ata3.00: failed to enable ATAPI AN (err_mask=0x4)
[   18.232081] ata3.00: failed to set xfermode (err_mask=0x40)
[   18.232131] ata3: limiting SATA link speed to 1.5 Gbps
[   18.232133] ata3.00: limiting speed to UDMA/33:PIO3
[   18.716014] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   28.728015] ata3.00: qc timeout (cmd 0xef)
[   28.728018] ata3.00: failed to enable ATAPI AN (err_mask=0x4)
[   28.728081] ata3.00: failed to set xfermode (err_mask=0x40)
[   28.728131] ata3.00: disabled
[   28.728136] ata3: hard resetting link
[   29.212014] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   29.212016] ata3: EH complete

```

Anyone have any idea what's going on ?

---

