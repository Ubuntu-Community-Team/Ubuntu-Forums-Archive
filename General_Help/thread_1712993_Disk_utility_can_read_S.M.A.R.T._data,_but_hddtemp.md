---
title: "Disk utility can read S.M.A.R.T. data, but hddtemp and smartctl can't"
date: 2011-03-23
forum: General Help
---

### Post by thoughtcriminall on 2011-03-23
I have a Western Digital "Green" hard drive (WDC WD20EARS-00MVWB0) inside an external enclosure and connected via USB. I want to keep an eye on the temperature, and when I use the Ubuntu Disk Utility GUI (System / Administration / Disk Utility), I can get the temp (and all other S.M.A.R.T. data) just fine. However, this drive will ultimately be used on a headless machine with no x server, so I need a CLI tool to read the temperature.

The drive is at /dev/sdb. When I run 
```
hddtemp /dev/sdb
```
It says "S.M.A.R.T. not available"

When I try
```
smartctl -a /dev/sdb
```
it says "Device does not support SMART."

Both hddtemp and smartctl correctly identify the drive as WDC WD20EARS-00MVWB0, but neither can read the SMART data.

What is the Disk Utility GUI doing that hddtemp and smartctl aren't doing? Is there a way to use the Disk Utility via the command line (on Ubuntu server edition, for example)?

---

### Post by tgalati4 on 2011-03-23
I was under the impression that SMART only worked on IDE/PATA and SATA interfaces, not USB.  Try plugging the drive into the machine using a direct cable, then try reading the SMART data.

---

### Post by thoughtcriminall on 2011-03-23
> **tgalati4 said:**
> I was under the impression that SMART only worked on IDE/PATA and SATA interfaces, not USB.

Thanks for the quick reply! If that's the case, I'm out of luck because the server this drive will be used for is a [tonido plug]("http://www.tonidoplug.com/") which only has USB and ethernet inputs.

However, I still don't understand why the Ubuntu Disk Utility GUI is able to read S.M.A.R.T. data for the drive even when connected over USB. That makes me think there should be some way to make it work.

---

### Post by tgalati4 on 2011-03-23
It may be simply the GUI is a python application that sends a data dump bit to the drive over USB and if the drive supports it, it will dump the data.  The smartctl utility is an older utility that does not support USB (from what I have read, I don't have direct experience with this issue).  I do plan on getting a tonido or guruplug to play with, so I will also be interested in a final solution.

It's also possible that the GUI is reading HAL or the /proc device tree for disk information, that looks similar to SMART data dump.  

You can look at the source code for the GUI and see what system command is invoked dumping the disk data.

The tonido plug is probably based on a Marvell chipset, so you could try:

sudo smartctl -a -d marvell /dev/sda

---

