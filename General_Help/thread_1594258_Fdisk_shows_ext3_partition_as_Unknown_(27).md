---
title: "Fdisk shows ext3 partition as Unknown (27)"
date: 2010-10-12
forum: General Help
---

### Post by nev3rm0re on 2010-10-12
When doing $sudo fdisk -l my /dev/sda1 (ext3, with Ubuntu 10.04 installed) shows up as Unknown.

GParted shows correct filesystem - ext3.

What can be the problem and how to fix it? I want fdisk to see my ext3 as ext3.

---

### Post by srs5694 on 2010-10-12
The fdisk utility doesn't look inside partitions; it only displays a partition type code that's part of the partition table itself. You can change this type code with the "t" command. For any Linux filesystem data, it should be set to "83", so do that. Short of modifying the fdisk source code and recompiling, there's no way to get fdisk to report the partition as "ext3," though; it'll just show up as "Linux" in the "System" column.

---

### Post by nev3rm0re on 2010-10-13
Thank you for an answer.

I had "diag" flag set on my linux partition, as soon as I removed it in GParted, fdisk started correctly reporting it as "Linux".

Can you explain how to change partition type code?

---

### Post by srs5694 on 2010-10-13
> **nev3rm0re said:**
> Thank you for an answer.

I had "diag" flag set on my linux partition, as soon as I removed it in GParted, fdisk started correctly reporting it as "Linux".

If so, then it's fixed now.

> Can you explain how to change partition type code?

See my previous post -- it's the "t" option in fdisk.

---

