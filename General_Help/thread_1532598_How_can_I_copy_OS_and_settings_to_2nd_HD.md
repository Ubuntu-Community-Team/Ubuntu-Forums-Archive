---
title: "How can I copy OS and settings to 2nd HD"
date: 2010-07-16
forum: General Help
---

### Post by CoolJohnB on 2010-07-16
I have two hard disks in my computer 160GB which has the file system and OS on it and 500GB which has all the Data on it.  I was thinking of swapping them over so that I have the OS and File System on the 500GB drive along with all the data and use the 2nd one for backup.    Therefore I wondered is there away to put the OS and associated software with all its upgrades onto the 500GB drive?  Or do I have to do a complete new install?  Any help will be much appreciated.  Thanks

---

### Post by bodhi.zazen on 2010-07-16
You can do this via many methods from dd to partimage to any number of live CD tools.

Perhaps the easiest is gparted on the Ubuntu desktop CD, it will "copy/paste" partitions.

After you move the partition you will likely need to update grub and perhaps fstab.

---

### Post by yaaarrrgg on 2010-07-16
Personally, I'd recommend keeping the data drive the largest, and keeping all data there.  Then if you do a clean install the data is unaffected.  It's hard to fill up 160GB with applications.  I've been using an external drive for backups.

"dd" might work, even to clone the master boot record, but I haven't tried it.

---

### Post by bodhi.zazen on 2010-07-16
> **yaaarrrgg said:**
> Personally, I'd recommend keeping the data drive the largest, and keeping all data there.  Then if you do a clean install the data is unaffected.  It's hard to fill up 160GB with applications.

"dd" might work, even to clone the master boot record, but I haven't tried it.

dd will do just fine =)

[http://www.debianhelp.co.uk/ddcommand.htm](http://www.debianhelp.co.uk/ddcommand.htm)

---

### Post by CoolJohnB on 2010-07-16
> **yaaarrrgg said:**
> Personally, I'd recommend keeping the data drive the largest, and keeping all data there.  Then if you do a clean install the data is unaffected.  It's hard to fill up 160GB with applications.  I've been using an external drive for backups.

"dd" might work, even to clone the master boot record, but I haven't tried it.

I think your right I just checked and I have 95GB of free space on that drive, so think it's best to leave well alone. Thanks for the suggestion of dd it looks like it will do the job if I ever decide to change.

---

