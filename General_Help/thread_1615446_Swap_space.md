---
title: "Swap space"
date: 2010-11-07
forum: General Help
---

### Post by AkiraBergman on 2010-11-07
I got a few Ubuntu versions on different partitions and a few 10G swap spaces on my 1TB disc. Is it possible to delete some of these swap spaces and just keep one? Will any of them do the job for all Ubuntu versions?

---

### Post by dcstar on 2010-11-07
> **AkiraBergman said:**
> I got a few Ubuntu versions on different partitions and a few 10M swap spaces on my 1TB disc. Is it possible to delete some of these swap spaces and just keep one? Will any of them do the job for all Ubuntu versions?

[LIST=1]
[*]Yes.
[*]Yes.
[/LIST]
You will have to change the UUID in all /etc/fstab files to use the common swap - search for detailed instructions.

---

