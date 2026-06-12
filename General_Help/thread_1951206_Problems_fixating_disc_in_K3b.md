---
title: "Problems fixating disc in K3b"
date: 2012-04-02
forum: General Help
---

### Post by schrammbo on 2012-04-02
Does anyone have any idea how to resolve this issue I am seeing with K3b?

Fixating...
Errno: 5 (Input/output error), flush cache scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 02 00 00
Sense Key: 0x0 No Additional Sense, Segment 11
Sense Code: 0x00 Qual 0x02 (end-of-partition/medium detected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 215.654s timeout 200s
[B]/usr/bin/wodim: Cannot fixate disk.
Trouble flushing the cache[/B]
Fixating time:  215.654s
/usr/bin/wodim: fifo had 3243 puts and 3243 gets.
/usr/bin/wodim: fifo was 0 times empty and 3033 times full, min fill was 96%.

---

