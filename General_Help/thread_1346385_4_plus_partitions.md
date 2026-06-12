---
title: "4 plus partitions"
date: 2009-12-05
forum: General Help
---

### Post by Mthbk1 on 2009-12-05
I tried this in xp and now in ubuntu.
Is there some way of getting more than four partitions on my hd?

---

### Post by egalvan on 2009-12-05
use extended partitions.
they can hold many more logical partitions.

---

### Post by Mthbk1 on 2010-01-21
Sorry I forgot to mention, I meant more than 4 'primary partitions' not logical :)

---

### Post by plucky on 2010-01-21
> **Mthbk1 said:**
> Sorry I forgot to mention, I meant more than 4 'primary partitions' not logical :)

No

4 primary partitions is the maximum.The extended partition counts as a primary partition.

---

### Post by bluefrog on 2010-01-21
yes you can have up to 128 primary partitions if memory serves but you need to set GPT label (gparted mklabel).

Prior to doing this make a backup of the existing data of the disk.

---

