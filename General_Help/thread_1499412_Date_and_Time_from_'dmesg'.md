---
title: "Date and Time from 'dmesg'"
date: 2010-06-01
forum: General Help
---

### Post by cmcginty on 2010-06-01
> Hi all,

Is there a way to change the Date and Time displayed when running the command 'dmesg'?

[413740.748385] sd 1:0:0:0: SCSI error: return code = 0x00040000
[413740.748392] end_request: I/O error, dev sdb, sector 586099263
[413740.748441] md: super_written gets error=-5, uptodate=0
[413740.748446] raid5: Disk failure on sdb1, disabling device. Operation continuing on 4 devices
[413740.786727] RAID5 conf printout:

This above example is rather cryptic. Why is does 'Ubuntu' {or Debian} display the date and time
this way? I guess it is in Julian date format.

Any info would be great.

Thanks,

Tim


I believe the dmesg format is in seconds from start of the system. You can covert it to your current "uptime" string using the following code:

```
date -u -d @{DMESG TIME}
```

For example:

```
$ date -u -d @1485979.091702
Sun Jan 18 04:46:19 UTC 1970
```

Basically this is the same as an uptime of: **17 days, 4 hours, 46 minutes, 19 seconds**

---

