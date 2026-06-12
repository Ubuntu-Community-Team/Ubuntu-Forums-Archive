---
title: "Abnormally slow boot?"
date: 2010-07-25
forum: General Help
---

### Post by xslntx on 2010-07-25
For some strange reason, since installing Ubuntu 10.04, my boot speeds have suffered rather severely. With 9.10, I had a running system in <15 seconds. With 10.04, it's more than doubled. I've noticed most of the time is spent waiting for the root filesystem, which is an Intel, striped fakeraid array.

Bootchart logs are attached. The first being one generated with Lucid, the second, I believe, was from 9.10.

I'm really at a loss as to how I can speed this process up. I'm fairly certain it isn't normal for the root filesystem to stall for a whole 30 seconds. 

Any ideas?

Edit: Attachments got resized.
With 10.04:
[http://i222.photobucket.com/albums/dd165/Difinity21/bryan-pc-lucid-20100725-5.png](http://i222.photobucket.com/albums/dd165/Difinity21/bryan-pc-lucid-20100725-5.png)

With 9.10:
[http://i222.photobucket.com/albums/dd165/Difinity21/b.jpg](http://i222.photobucket.com/albums/dd165/Difinity21/b.jpg)

Edit 2:
What seems to be the issue, according to dmesg:
> [    5.739393] scsi 5:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203N  SB01 PQ: 0 ANSI: 5
[    5.739502] scsi 5:0:0:0: Attached scsi generic sg4 type 5
[   30.033471] device-mapper: ioctl: device doesn't appear to be in the dev hash table.
[   30.033558] device-mapper: ioctl: device doesn't appear to be in the dev hash table.
[   30.315767] EXT4-fs (dm-3): mounted filesystem with ordered data mode


---

