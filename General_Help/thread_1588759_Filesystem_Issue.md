---
title: "Filesystem Issue"
date: 2010-10-05
forum: General Help
---

### Post by rockom on 2010-10-05
I've got a project where I'm pairing a fanless mini_ITX Intel Atom board  with a Micron 4GB eUSB SSD.  Works fine most of the time.  I've about a  hundred of these things built so far but I'm having an issue on some.   Here is what I get from time to time.

No GUI...very basic install  of Ubuntu 10.04.  Sometime during the night my filesystem crashes and  remounts read-only.  Here is what I see in the morning....

```
[44196.271993] end_request: I/O error, dev sda, sector 766992
[some number] Buffer I/O error on device dm-0, logical block 33166
[some number] Buffer I/O error on device dm-0, logical block 35236
[some number] Buffer I/O error on device dm-0, logical block 11850
[some number] end_request: I/O error, dev sda, sector 5448232
[some number] Buffer I/O error on device dm-0, logical block 618261
[some number] Aborting journal on device dm-0-8
[some number] Buffer I/O error on device dm-0, logical block 327680
[some number] JBD2: I/O error detected when updating journal superblock for dm-0-8
[some number] EXT4-fs error (device dm-0): ext4_journal_start_sb: Detected abort journal
[some number] EXT4-fs (dm-0): Remounting filesystem read_only
[some number] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[some number] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[some number] sd 3:0:0:0: [sdb] Assuming drive cache: write through
```

The numbers vary from system to system but the sequence of events is the same.
So, Do I have bad drives or is something wrong with my configuration?

Running versions 2.6.32-24

Thanks,
-Rocko

---

### Post by srs5694 on 2010-10-05
It looks like a hardware fault to me, but I'm not 100% positive of that. You could check the drives' SMART status using GSmartControl, smartctl, or something similar. That should turn up most faults within the hard disk; however, a bad cable, weak cable connection, or fault in the motherboard would not turn up in the SMART report, AFAIK. You could try swapping components around to localize such a problem. (It sounds like you've got lots of components, so this shouldn't be a fundamental problem -- it's just time-consuming.)

---

