---
title: "Ubuntu 10.04/Firefox/Hard Drive Partition issues"
date: 2011-04-18
forum: General Help
---

### Post by tinker1980 on 2011-04-18
I've been running Ubuntu for a little over a year now, upgraded to 10.04, and have been having zero troubles until last week. 

Last week, sadly enough, my wonderful linux machine started acting like... well... like it has Windows on it. I Have WinXP on another partition, and sometimes go to that partition to get files stored there, or to run WoW. I don't boot up windows, I just go to the partition (that "Side" of the drive, if you will) and load up files or run WoW in Wine. Hasn't been a problem, but last week it got to where when I try to mount the partition, the partition will mount, but the file manager (explorer? the part that lets me look at the files.) will get stuck. Screen will lose all it's color, it won't respond when I try to close it, and finally the file manager goes away, and all is ok. I can even open it back up and access the partition.

Another problem, bigger problem, is Firefox will sometimes get stuck. The color will go away in the firefox window, and it stops responding. If I click on the bar at the top of the screen (that has Applications/Places/System) then both the top and bottom bars will go away, I can't get to the terminal to restart gnome, the only thing I can do is reboot.

And just today, to top it all off, I can't start the computer normally. I'm reaching you from my backup hard drive. If I try to use my normal drive, I get a BOOT DISK FAILURE message. Computer works fine with this drive.

Could this just be a hardware problem? Should I now have an excuse to get a terabyte drive?:biggrin:

---

### Post by Irony on 2011-04-18
First off make sure you've backed up everything!

Start disk utility and see if the disk has errors on it.

---

### Post by tinker1980 on 2011-04-18
> **Irony said:**
> First off make sure you've backed up everything!

Start disk utility and see if the disk has errors on it.

I managed to get the computer to start with it's normal drive. I have run the disk utility, I'm going to run a self test next. The only thing I found that looked "Bad" was "Current Pending Sector Count". Also, when I mount my Windows partition, it won't scan it - says it's in use. If I unmount it, it says it's clean. 

Shows I have two bad sectors, which from what I remember isn't unusual.

EDIT: Now when trying to scan the other partition, the Disk Utility program just closes.

---

### Post by Irony on 2011-04-18
Try disk utility from a live cd.

---

### Post by srs5694 on 2011-04-18
Actually, if a SMART utility is reporting two bad sectors, that's bad. Such drives can sometimes shamble on for months or years, but even just two bad sectors can be a sign that the drive is on the verge of catastrophic failure. Note that all modern drives can map out bad sectors automatically and transparently, and one or two remappings of that type could indicate small manufacturing defects rather than real problems. SMART utilities only report bad sectors once the spare sector capacity has been exceeded, and this only happens if the disk has developed a large number of new bad sectors. Thus, if it says you've got two bad sectors, you've really got two bad sectors *in excess* of the capacity of the drive to handle them. Thus, I recommend replacing the drive immediately. Go to a brick-and-mortar store and buy one today. If that's impossible, shut down the computer and don't use it again until you've got a replacement in hand. Every minute you run that drive you risk more bad sectors showing up. I realize this sounds very alarmist, but if you're like most people, you probably have poor backups, so losing the drive catastrophically will be -- well -- catastrophic!

One other point: It sounds like your NTFS partition was not properly unmounted. This could account for some of your problems accessing it. You should run CHKDSK on it from Windows, since there are no good Linux NTFS-checking utilities. Given your bad drive, it's hard to be certain of the best way to proceed. Overall, it's probably best to copy the NTFS partition over and then check it on the new hard disk; but some copying methods might not work with the filesystem in an inconsistent state, so you might be forced to do the filesystem check before copying the partition.

---

### Post by tinker1980 on 2011-04-18
> **srs5694 said:**
> Actually, if a SMART utility is reporting two bad sectors, that's bad. Such drives can sometimes shamble on for months or years, but even just two bad sectors can be a sign that the drive is on the verge of catastrophic failure. Note that all modern drives can map out bad sectors automatically and transparently, and one or two remappings of that type could indicate small manufacturing defects rather than real problems. SMART utilities only report bad sectors once the spare sector capacity has been exceeded, and this only happens if the disk has developed a large number of new bad sectors. Thus, if it says you've got two bad sectors, you've really got two bad sectors *in excess* of the capacity of the drive to handle them. Thus, I recommend replacing the drive immediately. Go to a brick-and-mortar store and buy one today. If that's impossible, shut down the computer and don't use it again until you've got a replacement in hand. Every minute you run that drive you risk more bad sectors showing up. I realize this sounds very alarmist, but if you're like most people, you probably have poor backups, so losing the drive catastrophically will be -- well -- catastrophic!

One other point: It sounds like your NTFS partition was not properly unmounted. This could account for some of your problems accessing it. You should run CHKDSK on it from Windows, since there are no good Linux NTFS-checking utilities. Given your bad drive, it's hard to be certain of the best way to proceed. Overall, it's probably best to copy the NTFS partition over and then check it on the new hard disk; but some copying methods might not work with the filesystem in an inconsistent state, so you might be forced to do the filesystem check before copying the partition.

I wondered about the drive just being bad. I've had it for a very long time, it's from way back when a 320 gig SATA was the biggest and best. I've kinda upgraded the computer around it, and I could use an excuse to go get another drive. 

I have everything backed up on a spare (But smaller) hard drive, that I typically update once a month. Most of the time, however, the other drive just sits in the case disconnected. (Back in the day, I kept a copy on another drive like that in case something got on my normal drive I couldn't get rid of - then I could just format it and start over. It's not a problem with Ubuntu, but old habits die hard.)

Nice to know about the SMART telling me that the two bad sectors IN ADDITION to the capacity of the drive to work around them. Always good to learn something I didn't know.

---

