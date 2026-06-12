---
title: "Grub error 17"
date: 2010-05-15
forum: General Help
---

### Post by vuroth on 2010-05-15
running a dell inspiron 1720 laptop, dual booting ubunto (probably rev 9, not sure if I installed the latest uprev or not - probably not) and vista.  Powered it down this afternoon, now I can't boot it up at all - getting grub error 17.

I found an old 7.10live CD, but gparted and fdisk don't seem to find a linux partition, so I can't seem to boot EITHER windows OR ubuntu.

I really, really don't want to lose all my data under both linux AND windows, but I'm very worried/discouraged right now.

sudo fdsik -l gives something like

/dev/sda1 1 10 80293 de Dell Utility
/dev/sda2 11 1316 # 7 HPFS/NTFS
/dev/sda3 1316 10394 # 7 HPFS/NTFS
/dev/sda4 0395 19498 # f W95 Ext'd (LBA)

I *think* my linux partitions were in the extended partition, but why are they not reading?

---

