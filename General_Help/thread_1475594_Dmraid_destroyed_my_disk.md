---
title: "Dmraid destroyed my disk?"
date: 2010-05-07
forum: General Help
---

### Post by Groll on 2010-05-07
I did a clean installation of Ubuntu 10.04. Probably due to some bug, dmraid was recognizing two of my hard disks as being raid so I removed dmraid via the synaptic and then I installed Ubuntu on one of those disks. However now the partitions of my other disk (one NTFS and one ext3) are not recognized. Gparted shows the following message:

[[IMG]http://img197.imageshack.us/img197/2793/screenshotuz.th.png[/IMG]]("http://img197.imageshack.us/i/screenshotuz.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

Any ideas?

---

### Post by Groll on 2010-05-07
Bump

---

### Post by Groll on 2010-05-14
Anyone?

---

### Post by psusi on 2010-05-14
You should not just uninstall dmraid.  Either you are using a fake raid or you aren't.  If you aren't but the signatures are still on the drives then you need to remove them with dmraid -E.

It sounds like you were using fake raid and you installed Ubuntu to one of the disks in the raid, destroying the data that had previously been on that disk.

---

### Post by Groll on 2010-05-15
> **psusi said:**
> You should not just uninstall dmraid.  Either you are using a fake raid or you aren't.  If you aren't but the signatures are still on the drives then you need to remove them with dmraid -E.

It sounds like you were using fake raid and you installed Ubuntu to one of the disks in the raid, destroying the data that had previously been on that disk.
The data that were on the second disk were actually destroyed.

Is it possible the signatures have remained on the second disk so if I remove them I will me able to see my data? If yes how can I do that. I don't have dmraid installed now.

---

### Post by psusi on 2010-05-15
The signatures remain until you remove them with the bios raid utility or dmraid -E.  You destroyed your data when you overwrote it by installing the system on that drive.

---

