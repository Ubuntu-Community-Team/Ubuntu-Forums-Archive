---
title: "Force Mount"
date: 2010-12-31
forum: General Help
---

### Post by Mosabama on 2010-12-31
Hi,

I have a corrupted DVD and its very important, when ever I try to insert it .. the DVD icon Disappears .. or the computer will consider the DVD blank.

I took a look at /var/log/messages and it says that it cant read the partition table!

my question is :

is there a way to force mount the DVD even if its corrupted and make an image of the DVD using th dd command ? I mean to get what ever dd can read from the disk.

Thanks.

---

### Post by Mosabama on 2010-12-31
dmesg:

```

[59347.091524] sr 4:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[59347.091540] end_request: I/O error, dev sr0, sector 0
[59347.092222] sr 4:0:0:0: [sr0] Unhandled sense code
[59347.092228] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[59347.092234] sr 4:0:0:0: [sr0] Sense Key : Medium Error [current] 
[59347.092241] sr 4:0:0:0: [sr0] Add. Sense: Unable to recover table-of-contents
[59347.092251] sr 4:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[59347.092266] end_request: I/O error, dev sr0, sector 0
[59347.092280] UDF-fs: No anchor found
[59347.092285] UDF-fs: No partition found (1)


```

---

### Post by Mosabama on 2011-01-01
up

---

