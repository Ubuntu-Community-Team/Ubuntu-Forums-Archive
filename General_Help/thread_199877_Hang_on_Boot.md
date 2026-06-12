---
title: "Hang on Boot"
date: 2006-06-19
forum: General Help
---

### Post by dnel on 2006-06-19
hi,
I'm having a problem with my Ubuntu install hanging on boot at the "Loading Hardware Drivers" point. It doesn't hang every time although it happens in about 4 out of 5 attempts. 

In my /var/log/messages file I get a lot of these which might be the culprit

```
Jun 18 17:20:13 monster kernel: [17179619.808000] hdb: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=78230639, sector=78165360
Jun 18 17:20:13 monster kernel: [17179619.808000] ide: failed opcode was: unknown
Jun 18 17:20:13 monster kernel: [17179619.952000] ide0: reset: success
Jun 18 17:20:13 monster kernel: [17179620.124000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jun 18 17:20:13 monster kernel: [17179620.124000] hdb: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=78230639, sector=78165360
Jun 18 17:20:13 monster kernel: [17179620.124000] ide: failed opcode was: unknown
Jun 18 17:20:13 monster kernel: [17179620.124000] end_request: I/O error, dev hdb, sector 78165360
Jun 18 17:20:13 monster kernel: [17179620.396000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jun 18 17:20:13 monster kernel: [17179620.396000] hdb: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=78230639, sector=78165360
Jun 18 17:20:13 monster kernel: [17179620.396000] ide: failed opcode was: unknown
Jun 18 17:20:13 monster kernel: [17179620.568000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jun 18 17:20:13 monster kernel: [17179620.568000] hdb: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=78230639, sector=78165360
```

Ignoring "monster" as that's the name of the computer not the problem :)

Before I reinstall the OS on a different hard disk, has anyone any clue what might be causing these errors and whether they are fixable?

FYI the drive is formatted reiserfs in a single partition + swap whether that's relevent.

TIA
dnel

---

