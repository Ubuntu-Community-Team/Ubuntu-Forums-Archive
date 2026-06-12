---
title: "ATA exceptions in dmesg"
date: 2010-09-25
forum: General Help
---

### Post by whereami8224 on 2010-09-25
I just installed Ubuntu 10.10 (maverick) beta on my new Dell Studio XPS 9100 system. The SATA controller is an Intel 82801JI.

Is this a SATA driver problem? I'm afraid this might mean the disk is bad, although Windows [0] isn't having any problems. I thought I'd ask some pros before I call Dell tech support to get the disk replaced.

Thanks!

Full dmesg output is available here: [http://pastebin.com/uc6dZsnt](http://pastebin.com/uc6dZsnt)

Here's a typical snippet from dmesg:
```

[  250.639510] ata3.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
[  250.639556] ata3.00: irq_stat 0x40000008
[  250.639585] ata3.00: failed command: READ FPDMA QUEUED
[  250.639625] ata3.00: cmd 60/00:08:38:3f:4b/01:00:13:00:00/40 tag 1 ncq 131072 in
[  250.639626]          res 41/40:00:c1:3f:4b/00:00:13:00:00/40 Emask 0x409 (media error) <F>
[  250.639697] ata3.00: status: { DRDY ERR }
[  250.639711] ata3.00: error: { UNC }
[  250.644183] ata3.00: configured for UDMA/133
[  250.644194] sd 2:0:0:0: [sda] Unhandled sense code
[  250.644196] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  250.644199] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  250.644206] Descriptor sense data with sense descriptors (in hex):
[  250.644207]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  250.644211]         13 4b 3f c1 
[  250.644213] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  250.644216] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 13 4b 3f 38 00 01 00 00
[  250.644220] end_request: I/O error, dev sda, sector 323698625
[  250.644247] ata3: EH complete

```

[0] I'm only running Windows until I can get a stable Linux installed. I haven't really used Windows in years...

---

### Post by dcstar on 2010-09-26
> **whereami8224 said:**
> I just installed Ubuntu 10.10 (maverick) beta on my new Dell Studio XPS 9100 system. The SATA controller is an Intel 82801JI.

Is this a SATA driver problem? I'm afraid this might mean the disk is bad, although Windows [0] isn't having any problems.


Windows is not using the part of the disk that Linux is.

Use the Disk Utility to do a full SMART test on the disk.

---

### Post by whereami8224 on 2010-09-26
Indeed, it does fail a surface test. Rather quickly, too. It's not very informative, though. All it says is "FAILED (Read)".

That's wonderful, now I'll have to deal with tech support, and convince them I know what I'm talking about.

Thanks for the help.

---

### Post by whereami8224 on 2010-09-26
> **whereami8224 said:**
> That's wonderful, now I'll have to deal with tech support.

I have to eat my words. That was too easy. New disk on its way.

---

