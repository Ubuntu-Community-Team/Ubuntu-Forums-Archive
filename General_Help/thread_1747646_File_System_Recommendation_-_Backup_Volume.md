---
title: "File System Recommendation - Backup Volume"
date: 2011-05-02
forum: General Help
---

### Post by re1d on 2011-05-02
System76 laptop, 10.04, 320GB HDD, _VMware with Win7 in one VM_; want to  use Clonezilla as am using it to back up (bare metal backup image) another older smaller dual-boot  Ubuntu/XP machine. 

This System76 laptop is a work machine that I control; the Win7 VM only  does a couple of things but they're necessary for work and I don't want to lose the configuration. The reason for the bare metal backup is so if I have to, I can restore and get back to work - something I've had to do on some previous occasions back when I used Windows. Data is no problem - I back that up separately on an hourly basis.

My question is **what FS to use on the backup drive**; for instance, for the  dual-boot XP/Linux work machine I'm currently backing up, I'm using a  30GB external HDD formatted in FAT32. That's OK because 30GB is below the  limit for FAT32. But for the newer laptop I'll need a much bigger backup  partition. I chose FAT32 for the old one because I know everything on  the computer being backed up, Windows & Linux both, is compatible  with it. 

But what FS should I use to back up the new laptop, considering that I'll be  backing up the Win7 VM as well as the main Linux part of the machine? I plan  to use a backup partition of about 160GB. Could I format it NTFS and  have it work with Ubuntu 10.04? Or, conversely, if I format it EXT, will  it back up the Win7 VM OK?

Hope it's not a dumb question - didn't see a reference to it anywhere else. Thanks!

---

### Post by edm1 on 2011-05-03
Not ideal but I think you'll have to go NTFS as linux now has pretty good support for it whereas Windows does not support EXT. I think Windows may support EXT3 through 3rd party drivers but I wouldnt trust them a great deal.

---

