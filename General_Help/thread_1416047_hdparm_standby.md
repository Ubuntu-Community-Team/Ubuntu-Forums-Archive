---
title: "hdparm standby"
date: 2010-02-25
forum: General Help
---

### Post by tanha on 2010-02-25
I used the following command to put my backup hdd into standby:

```
# hdparm -y /dev/sdb1

/dev/sdb1:
 issuing standby command

```

check the status:

```
# hdparm -C /dev/sdb1

/dev/sdb1:
 drive state is:  standby

```

and a few seconds later:

```
# hdparm -C /dev/sdb1

/dev/sdb1:
 drive state is:  active/idle

```

It does this every time. What would cause the disk to spin up when it's not even in use?

---

### Post by dabl on 2010-02-25
Mount options like "relatime", among other things.

Here's some relevant info:  [http://www.lesswatts.org/tips/disks.php](http://www.lesswatts.org/tips/disks.php)

---

### Post by tanha on 2010-02-25
> **dabl said:**
> Mount options like "relatime", among other things.

Here's some relevant info:  [http://www.lesswatts.org/tips/disks.php](http://www.lesswatts.org/tips/disks.php)

Thank you.

---

### Post by tanha on 2010-02-25
When ever it wakes up, I get these messages in syslog:

```
Feb 25 16:55:54 mara kernel: [18435.011268] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Feb 25 16:55:54 mara kernel: [18435.011274] ata2.00: cmd b0/d8:00:00:4f:c2/00:00:00:00:00/00 tag 0
Feb 25 16:55:54 mara kernel: [18435.011275]          res 40/00:00:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
Feb 25 16:55:54 mara kernel: [18435.011276] ata2.00: status: { DRDY }
Feb 25 16:55:54 mara kernel: [18435.011279] ata2: hard resetting link
Feb 25 16:55:59 mara kernel: [18440.410019] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb 25 16:56:00 mara kernel: [18440.895019] ata2.00: configured for UDMA/133
Feb 25 16:56:00 mara kernel: [18440.895036] ata2: EH complete
```

Does anyone know what this means?

---

