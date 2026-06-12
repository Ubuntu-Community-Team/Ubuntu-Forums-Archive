---
title: "dmraid monitoring"
date: 2009-11-09
forum: General Help
---

### Post by fermulator on 2009-11-09
Anyone know of an application that can monitor the state of a dmraid (fake raid) array?

I know mdadm software RAID has scripts and such, but I'm not aware of any monitoring script for dmraid.

Even better would be a GNOME Applet for Ubuntu which could provide a nice GUI interface for a user who has a RAID1 setup, or RAID0, etc.

---

### Post by WilliamThrilliam on 2010-07-13
Wow, this would be awesome!  I recently didn't had to rebuild a raid 1 set in 10.04 because of a bug in dmraid.  I didn't know it until I restarted my computer and just happened to spy "REBUILD" on my ich9r bios.

---

### Post by trgraglia on 2010-10-18
I have a RAID 1 in BIOS and it had a failure. It says rebuild now and it wont rebuild. How do I tell it to rebuild from Linux? Looks like William did it but Im not sure if his was set up in the OS or the BIOS...

Thanks ahead of time.

---

### Post by Rafa&#322; Rudowski on 2011-02-16
> **trgraglia said:**
> I have a RAID 1 in BIOS and it had a failure. It says rebuild now and it wont rebuild. How do I tell it to rebuild from Linux? Looks like William did it but Im not sure if his was set up in the OS or the BIOS...

Thanks ahead of time.

Command:
*[COLOR="DarkSlateGray"]dmraid -help|grep rebuild*
[/COLOR]shows only one line:[COLOR="DarkSlateGray"] [I]
dmraid	{-R|--rebuild} RAID-set [drive_name][/I] [/COLOR]

Currently, I'm creating NVidia Raid 1. Before inserting the relevant data, I'll simulate loss of one disk and try data recovery on OS (from BIOS I don't think it's possible, at least on NVidia Raids becouse it is fakeRaid). If I get lucky I'll post the solution (although you probably don't nead it anymore).

BTW I don't see mutch help on the web about Raid 1 recovery procedure for degraded Raid status (fakeRaid on Ubuntu of course).

---

### Post by WilliamThrilliam on 2011-02-16
Hello,

I had to boot into windows and install intel's raid utility to be able to rebuild.  I wish dmraid would do this. Intels utility did work however, maybe we can get them to contribute to dmraid.

---

