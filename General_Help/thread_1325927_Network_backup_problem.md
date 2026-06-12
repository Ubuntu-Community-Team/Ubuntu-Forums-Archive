---
title: "Network backup problem"
date: 2009-11-13
forum: General Help
---

### Post by memilanuk on 2009-11-13
So... got an old PC online and running as a Linux file server, running ssh and samba.  Main OS is on a 13.8GB PATA drive, with a 12.2GB / partition, and a 1.5GB partition for swap.  There are two 500GB SATA drives set up in a software RAID 1 configuration mounted under /srv.  I have BackupPC running, and I am trying to get the initial full backup done.  Unfortunately this is proving to be more of a PITA than I had anticipated.

The network layout is like this: PPPOE over fiber to the ISP.  I have a Buffalo wifi router/access point plugged into the wall, connected to the ISP.  I have the following connected via 802.11g wireless: a Macbook (mine), another Macbook (wife's from the school district), the daughter's HP laptop (when she's home), and my main HP desktop PC (actually this has an Atheros a/b/g/n dual channel wireless adapter, but the main network is 802.11g).  Also connected to the wifi router via a cat5 ethernet cable to one of the LAN ports is the server.

The plan *was* to backup the 'Users' directory on the desktop PC, the HP laptop, and the two macboooks... and then perhaps use the 'Archive' function of BackupPC to an external hard drive for a little additional peace of mind.

The problem is... the drive capacities are huge relative to the network speeds I'm getting.  The desktop has a 640GB hard drive, and the laptop has a 500GB hard drive.  The two macbooks have 40-60GB hard drives, but they are both getting close to end of life.  The two larger machines aren't anywhere near full, but even after setting the config.pf file for BackupPC to skip any CD/DVD images, Virtualbox disk images, or TrueCrypt volumes, the remainder on the desktop PC is considerable - lots of pictures and videos and a metric crap load in the iTunes directory ;)  With a *peak* transfer rate from the PC of about 20 Mbit/s, and average somewhere below 15... well, the Atheros wifi adapter has locked up about five times already, requiring me to restart the full backup :mad:

Once it gets done - if it gets done... subsequent incremental backups shouldn't be so bad - until I download another seasons worth of a television series :rolleyes: .  

I figure I can hook the laptops up via ethernet and speed things up considerably, at least for that first full backup.  Would doing the transfer over ssh/rsync be noticeably faster than using Samba, considering the weak link seems to be the wifi connection?  I've also thought of going ahead and getting that external drive I mentioned earlier, backing up to it from the PC and then using it to 'pre-seed' the backup directory on the server.  If it worked the way I'm picturing in my mind, it'd be a fairly convoluted evolution, and definitely not something I'd want to do on a regular basis.  If anyone has any ideas or suggestions short of packing up the desktop PC and hauling it downstairs to hook up to the router via cat5... I'm open.

---

### Post by memilanuk on 2009-11-14
BTT...

For all the people in these forums who say they use BackupPC and recommend it, I'm surprised no one has any ideas on the matter...

---

