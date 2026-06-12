---
title: "libata-ignore_hpa=1"
date: 2010-06-23
forum: General Help
---

### Post by magnum696 on 2010-06-23
All,

I'm looking to stop ubuntu from unlocking HPA on my raid drive.  I have ubuntu 10.04 installed on a seperate, non-RAID drive and it keeps messing of my 'fakeRAID' when it performs the unlock.  Does anyone know how to make libata stop doing this?

Here is how it looks in my kern.log.  I have 2 drives in RAID 0 and it seems to just unlock 1 of them.

Jun 22 11:00:37 peter-desktop kernel: [    1.324866] ata3.00: **[COLOR=black]HPA unlocked: 312579695 -> 312581808, native 312581808[/COLOR]**
Jun 22 11:00:37 peter-desktop kernel: [    1.324871] ata3.00: ATA-7: ST3160815AS, 4.AAA, max UDMA/133
Jun 22 11:00:37 peter-desktop kernel: [    1.324874] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jun 22 11:00:37 peter-desktop kernel: [    1.357766] ata3.00: configured for UDMA/133
Jun 22 11:00:37 peter-desktop kernel: [    1.370072] scsi 2:0:0:0: Direct-Access     ATA      ST3160815AS      4.AA PQ: 0 ANSI: 5
Jun 22 11:00:37 peter-desktop kernel: [    1.370171] sd 2:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Jun 22 11:00:37 peter-desktop kernel: [    1.370201] sd 2:0:0:0: [sdb] Write Protect is off
Jun 22 11:00:37 peter-desktop kernel: [    1.370202] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Jun 22 11:00:37 peter-desktop kernel: [    1.370218] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

### Post by dino99 on 2010-06-23
some links about

[http://www.google.com/search?hl=fr&lr=lang_en&tbs=qdr%3Ay%2Clr%3Alang_1en&q=%22libata-ignore_hpa%3D%22%2Blucid&btnG=Rechercher&aq=f&aqi=&aql=&oq=&gs_rfai=](http://www.google.com/search?hl=fr&lr=lang_en&tbs=qdr%3Ay%2Clr%3Alang_1en&q=%22libata-ignore_hpa%3D%22%2Blucid&btnG=Rechercher&aq=f&aqi=&aql=&oq=&gs_rfai=)

---

