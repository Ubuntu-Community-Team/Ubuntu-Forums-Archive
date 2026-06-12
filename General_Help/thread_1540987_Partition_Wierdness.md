---
title: "Partition Wierdness"
date: 2010-07-28
forum: General Help
---

### Post by zozza on 2010-07-28
In Gparted I have a Windows NTFS partition, a Linux ext3 partition, and a Linux swap partition. 

I also have unallocated space.   This is all fine.  

However, I also interestingly have on /dev/sda3 (which is not mounted) a FAT32 partition of 5GB of which about half is used with the label "PE" and the flags "hidden, lba".  

According to [http://www.datarecovery.com/hexcodes.asp](http://www.datarecovery.com/hexcodes.asp) it is a hidden Windows partition - Windows hidden Windows95 FAT32 partition (LBA-mode).

How can I see what this contains?  How was it created?

Also, I have on /dev/sda4 47MB of "unknown" material.  This is also unmounted.  The Palimpsest Disk Utility says the type is EFI (FAT-12/26/32 (0xef).  I understand that EFI is a type of Ubuntu partition but in which case why is it "unknown" rather than something normal for Ubuntu?


What is this EFI partition?  

Thanks!

---

### Post by prodigy_ on 2010-07-28
> a FAT32 partition of 5GB
Probably a system restore partiton created by your PC vendor.

What is this EFI partition? 
[http://en.wikipedia.org/wiki/Extensible_Firmware_Interface#Extensions](http://en.wikipedia.org/wiki/Extensible_Firmware_Interface#Extensions)

---

### Post by Nytram on 2010-07-28
I've also got a PE partition with the same specs as yours, it's for recovering windows.

---

