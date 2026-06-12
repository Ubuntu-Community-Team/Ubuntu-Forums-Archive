---
title: "Ext3 or ext4??"
date: 2010-07-09
forum: General Help
---

### Post by ve2 on 2010-07-09
Does it make a difference? I have read so much downsides to EXT4.... is it ready yet?:KS

---

### Post by Woody1987 on 2010-07-09
EXT3 - stable/slow
EXT4 - fairly stable/fast

I personally go for ext4. I have never had any problems.

---

### Post by BikeHelmet on 2010-07-09
I usually go ext2. The speed difference seems minimal, and if something craps out, at least I can read the partition from another OS. (Including Windows)

---

### Post by Woody1987 on 2010-07-09
> **BikeHelmet said:**
> I usually go ext2. The speed difference seems minimal, and if something craps out, at least I can read the partition from another OS. (Including Windows)

EXT3 is the same as EXT2 but with journalling, making it more stable.

---

### Post by BikeHelmet on 2010-07-09
> **Woody1987 said:**
> EXT3 is the same as EXT2 but with journalling, making it more stable.

Journaling, plus a different size for [something] that makes it unreadable in FreeBSD/FreeNAS and older LiveCDs.

My computer has an older PATA controller, which had its support cut with 9.10+; to access stuff on my one PATA drive, I have to use older kernel versions. But most LiveCDs (except an older release of Ubuntu) can't read Ubuntu's ext3. :P The easiest solution was ext2, and then I can access it from Windows.

---

### Post by audiomick on 2010-07-09
I have had no problems with EXT4, but I have no older hardware, and don't  need to access from Windows either.

---

