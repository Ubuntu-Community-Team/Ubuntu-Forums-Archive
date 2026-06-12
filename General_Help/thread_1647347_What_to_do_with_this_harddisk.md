---
title: "What to do with this harddisk?"
date: 2010-12-17
forum: General Help
---

### Post by stefangr1 on 2010-12-17
I'm having some trouble with one of my system harddisks. It sometimes works without problems, but is not mounted on other occasions. Even when it's mounted, it's working extremely slow and programs using files from it may crash. On other occasions, however, there are no problems at all. If it's not automounted, I may be able to mount it manually but it sometimes shows "UUID not found".

If has a lot of SMART errors: ```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   076   076   011    Pre-fail  Always       -       7970
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       699
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       11725
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       5510
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       699
 13 Read_Soft_Error_Rate    0x000e   100   100   000    Old_age   Always       -       0
183 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
184 Unknown_Attribute       0x0033   025   025   000    Pre-fail  Always       -       75
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   074   060   000    Old_age   Always       -       26 (Lifetime Min/Max 26/26)
194 Temperature_Celsius     0x0022   073   059   000    Old_age   Always       -       27 (Lifetime Min/Max 26/27)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       40916
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       946
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       1
201 Soft_Read_Error_Rate    0x000a   253   253   000    Old_age   Always       -       0

```

If it seems to be working well, I can run a SMART selftest and it shows no errors. If it's giving trouble, however, it shows "Iterrupted (host reset)".

If it fails, the following errors are shown in my syslog:```

Dec 17 11:28:08 linux kernel: [  438.586373] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Dec 17 11:28:08 linux kernel: [  438.586376] ata3.00: BMDMA stat 0x66
Dec 17 11:28:08 linux kernel: [  438.586384] ata3.00: cmd c8/00:38:47:2c:46/00:00:00:00:00/ef tag 0 dma 28672 in
Dec 17 11:28:08 linux kernel: [  438.586385]          res 51/84:27:58:2c:46/84:00:44:00:00/ef Emask 0x30 (host bus error)
Dec 17 11:28:08 linux kernel: [  438.586389] ata3.00: status: { DRDY ERR }
Dec 17 11:28:08 linux kernel: [  438.586392] ata3.00: error: { ICRC ABRT }
Dec 17 11:28:08 linux kernel: [  438.586399] ata3: soft resetting link
Dec 17 11:28:08 linux kernel: [  438.800338] ata3.00: configured for UDMA/33
Dec 17 11:28:08 linux kernel: [  438.820340] ata3.01: configured for UDMA/133
Dec 17 11:28:08 linux kernel: [  438.820346] ata3: EH complete

```

Is my harddisk dying? Will the fact that it's still working to some extend get me in trouble with the warrenty? Or could this be something else...

EDIT: I just noticed that some of the values in the latest SMART output seem to be reset. The number of ECC recovered errors was previously about 4 million, and the min/max temperatures were in the usual range (8/40 or so).

---

### Post by oldos2er on 2010-12-17
I would back up any sensitive data from that drive now, if I were you.

---

### Post by stefangr1 on 2010-12-17
> **oldos2er said:**
> I would back up any sensitive data from that drive now, if I were you.

Luckily I have a backup of all the data on this particular disk, or more accurate: this is one of the harddisks I'm using for my backups.

---

### Post by dabl on 2010-12-17
Sometimes an early symptom of aging is that a cold hard drive won't spin up to speed fast enough to satisfy the bootloader, and it is "dropped" during the boot process.  Also, if its speed is marginal for awhile after starting the computer, it might not be read correctly.

If that drive runs OK after it warms up for an hour (you can use "sudo mount -a" to mount it if it is listed in /etc/fstab), I would copy all the valuable data off to a newer drive.  Then it might work as a paperweight, or in a sock it would make a decent weapon.  :D

---

### Post by stefangr1 on 2010-12-18
I've now replaced the cable and connected the harddisk to a different SATA port. It's now working again, but some files have been corrupted. I had verified before that the cables weren't lose, but when I wanted to get it out yesterday I noticed that one of the connectors had a bit of an oval shape.

After replacing it, it seems to work again and there are no longer errors occuring in my syslog. However, data written in between was corrupted (TimeMachine dealt with this in it's own peculiar way, by deleting all it's backups :) ).

Small question: should I worry about the consistency of the filesystem?

---

### Post by Krytarik on 2010-12-18
I would check them with GParted, just in case.

---

### Post by cgroza on 2010-12-18
Sometimes we need to buy a new HDD. Oh well, thats life.

---

### Post by stefangr1 on 2010-12-19
> **cgroza said:**
> Sometimes we need to buy a new HDD. Oh well, thats life.

Sometimes we do, but I suspect that in this case it was really a bad cable. The reason I had some doubts about whether the disk was dying or not was the combination of sometimes extreme failure (not even detected or crashing nautilus after copying 1kb in one minute), and sometimes working fine and returning "success" after an extended 2 hour SMART self test.

If this hdd was critical I might replace it, but as I already keep automated backups of all my data I guess I'll keep it.

---

