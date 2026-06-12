---
title: "ext4 journal"
date: 2011-09-21
forum: General Help
---

### Post by Linux_junkie on 2011-09-21
I may have the wrong idea about this but I've read that ext2/3/4 are journalled file systems.  I am asuming then that there is a file somewhere in the system detailing all disk activity.  If so, is there a way of accessing this journal in the system?

---

### Post by kimda on 2011-09-21
ext3 and ext4 are journalled file systems. You can use debugfs command with logdump option to view journal logs.

---

### Post by Linux_junkie on 2011-09-21
> **kimda said:**
> ext3 and ext4 are journalled file systems. You can use debugfs command with logdump option to view journal logs.

Thank you

---

