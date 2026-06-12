---
title: "SATA errors on new installation"
date: 2011-08-04
forum: General Help
---

### Post by Dunge on 2011-08-04
I have a Asus P8P67 Pro B3 motherboard (very recent), one Western Digital Raptor 150GB 10k RPM drive  with Windows on it and a Western Digital Cavior Black 1TB drive I had NTFS data on it, resized part of it and installed Ubutu 11.04 x64 on a new partition there. 

Everything under Ubuntu is slow as hell and the hard drive seems to hang if two process access the disk at the same time. Opening a terminal or Firefox windows can take up to 10minutes. Never had any problem of any kind when using the disk under Windows. I did a full scandisk in Windows, then booted on Ubuntu live CD and forced a fsck on the Ubuntu partition, everything seems fine. SMART status looks fine too. When it's not "frozen", hdparm give good results:

/dev/sda:
 Timing cached reads:   27522 MB in  2.00 seconds = 13774.76 MB/sec
 Timing buffered disk reads: 302 MB in  3.02 seconds = 100.03 MB/sec

On the other end, dmesg give me a bunch of these scary messages. Anyone can find out where the problems lies? :

[ 1209.494129] ata1.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
[ 1209.494134] ata1.00: irq_stat 0x40000008
[ 1209.494137] ata1.00: failed command: READ FPDMA QUEUED
[ 1209.494143] ata1.00: cmd 60/08:08:28:45:54/00:00:6b:00:00/40 tag 1 ncq 4096 in
[ 1209.494145]          res 41/40:00:2d:45:54/00:00:6b:00:00/40 Emask 0x409 (media error) <F>
[ 1209.494148] ata1.00: status: { DRDY ERR }
[ 1209.494150] ata1.00: error: { UNC }
[ 1209.495713] ata1.00: configured for UDMA/133
[ 1209.495722] ata1: EH complete

---

### Post by Dunge on 2011-08-04
Please advise?

---

### Post by psusi on 2011-08-04
Your drive has bad sectors.  Take a look at the SMART stats in the disk utility.

---

### Post by Dunge on 2011-08-04
Well actually yes it have a 83 "Current Pending Sector Count" since nearly a year. It's still a warning. Hadn't increased and hadn't prevented me to use the disk at his fullest capacity either. I copied and delete gigabytes and gigabytes on it since with no errors. These bad sectors are supposed to be marked bad and not used anymore when a scandisk is performed anyway, why would it prevent Ubuntu to do anything at all!? I can't use the disk at all under Ubuntu, it just freeze when I click anything. Under Windows, I still copied tons of data on it today no problems. This don't look like a bad disk, it look like bad driver modules to me.

---

### Post by dcstar on 2011-08-05
```
man badblocks
```

---

### Post by psusi on 2011-08-06
No, 83 pending sectors means you have 83 bad sectors.  You can use badblocks to identify which ones are bad and then try to write zeros to them with dd.  This will force the drive to try to write to the sector, which may work and correct the problem, or it will remap the sector to one from the spare pool.  If you can get the pending count down to zero, and still have zero in the offline_uncorrectable and reallocated counts, then you have corrected the problem.  If not, you need to RMA the drive.

---

