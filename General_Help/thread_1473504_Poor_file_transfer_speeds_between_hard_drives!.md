---
title: "Poor file transfer speeds between hard drives!"
date: 2010-05-05
forum: General Help
---

### Post by jshuford on 2010-05-05
After trying MANY of the posted suggestions here with regards to the above mentioned problem...I have found a result that seems to work nicely so I thought that I would share my findings;

Starting with an 8.4gb file (VMWare Virtual Machine)

Data transfer speeds between two hard drives had always started out speedy 30.3mb/sec then soon slowed down to approximately 1.7mb/sec... (eternity!)

Now I transfer the same file at start: 60.3mb/sec and the file slows to approximately 35.7mb/sec... (1.93 minutes)

"hdparm" was used to disable write-caching and I changed the receiving HDD's format to ext3/ext4...

If anyone has any thoughts or comments please post them here so I can be better informed as to what I have done!

Thank you :)

[email]jshuford@gmail.com[/email]

---

### Post by StuartN on 2010-05-05
> **jshuford said:**
> "hdparm" was used to disable write-caching and I changed the receiving HDD's format to ext3/ext4...

1) Do you mean you reformatted the receiving drive? Either ext3 or ext4 is okay? (I find ext4 distinctly slower for large file copies).

2) Can you post a sample command. Is this permanent or per-session?

---

### Post by jshuford on 2010-05-05
> **StuartN said:**
> 1) Do you mean you reformatted the receiving drive? Either ext3 or ext4 is okay? (I find ext4 distinctly slower for large file copies).

2) Can you post a sample command. Is this permanent or per-session?

=1) Yes I reformatted the receiving HDD to ext3/ext4

=2) "root@*********:/home/****#hdparm -W 0 (0=on/1=off) /dev/sdb

** -W   get/set drive write-caching flag (0/1)"

[http://www.seagate.com/ww/v/index.jsp?vgnextoid=20b92d0ca8dce110VgnVCM100000f5ee0a0aRCRD](http://www.seagate.com/ww/v/index.jsp?vgnextoid=20b92d0ca8dce110VgnVCM100000f5ee0a0aRCRD)

Model=ST31000528AS, FwRev=CC34, SerialNo=********
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=disabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7


I believe that the setting is permanent (for the current login/user) until I change it manually!

---

### Post by dino99 on 2010-05-05
i hope you are aware about that: "hdparm" was used to disable write-caching

better to not have a power failure :lolflag:

ext3 or ext4 : same story

---

### Post by jshuford on 2010-05-05
> **dino99 said:**
> i hope you are aware about that: "hdparm" was used to disable write-caching

better to not have a power failure :lolflag:

ext3 or ext4 : same story

Well my system will finish what it is doing and shut-down gracefully,use an "UPS"...Thank you ):P

---

### Post by psusi on 2010-05-05
Disabling the write cache will SLOW things down.  Caches exist to speed things up.

And ext4 handles large files much better because it uses extents instead of block lists.

---

### Post by jshuford on 2010-05-05
> **psusi said:**
> Disabling the write cache will SLOW things down.  Caches exist to speed things up.

And ext4 handles large files much better because it uses extents instead of block lists.

I was wondering if by doing both things if I had actually done something that would work until I figured something else out?

---

### Post by dino99 on 2010-05-05
> **jshuford said:**
> I my system will finish what it is doing and shut-down gracefully,use an "UPS"...Thank you ):P

dont forget read/write flaws problems too, i will never do that anyway

---

### Post by jshuford on 2010-05-05
Well; at best the idea seems risky, but I think that the trade-off between file security/integrity and transfer speeds may be worth the risk in this instance.

If the transfer should somehow be blown then I would always have the original file to rely on to attempt the transfer again.

If anyone could help me with a better way I would gladly listen and try the technique for myself...

---

