---
title: "Is this ext3 format taking too long?"
date: 2010-08-30
forum: General Help
---

### Post by ownaginatious on 2010-08-30
So I'm formatting a RAID 5 I build on a Raid Rocket 2301 RAID card of four 2 TB hard drives. I'm formatting with a GPT partition table into ext3 using gparted... and so far it has been about 30 minutes.

Is this too long? I can't tell if the mkfs process froze or not :p.

---

### Post by srs5694 on 2010-08-30
Creating an ext2/3/4 filesystem can take a while. I've never done it on anything close to 8 TB, but my suspicion is that it could take over 30 minutes. If it hasn't completed after three or four hours, it may be time to be concerned.

---

### Post by ricardisimo on 2012-10-12
ext4 takes no time at all with gparted, but ext3... wow. 250GB took several minutes, whereas it was a few seconds with ext4.

---

