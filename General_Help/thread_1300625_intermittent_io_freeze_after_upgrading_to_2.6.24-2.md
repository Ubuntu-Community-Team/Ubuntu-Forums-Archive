---
title: "intermittent i/o freeze after upgrading to 2.6.24-25"
date: 2009-10-25
forum: General Help
---

### Post by lvm on 2009-10-25
Hardy 64, today I've upgraded to 2.6.24-25 kernel, since then system froze twice with the symptoms which suggest some major disk access problem: running apps keep running fine until they try to access a disk file, after that they may become sluggish or lock up completely, attempts to start new programs may not succeed. CPU usage is very low, no swapping at all. On one occasion I was coping a file from the affected system over samba, the copy process didn't die completely but the speed dropped dramatically and remained more or less constant.

After 2-3 minutes normal operations resume, all programs I've tried to start during the freeze period do start, etc, and theres is nothing to show that something was wrong, nothing in the logs at all, disk SMART shows no problems either. Any ideas?

---

