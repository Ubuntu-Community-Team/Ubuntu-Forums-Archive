---
title: "Moving /opt to another drive"
date: 2010-06-06
forum: General Help
---

### Post by Theobalt on 2010-06-06
Hi!

I'd like to move the /opt directory to another partition (the one where /home already lies). How can I do that? Can I use the same process to move any directory to any partition/drive?

Thank you very much.

---

### Post by Theobalt on 2010-06-07
bump

---

### Post by oldos2er on 2010-06-07
Assuming you have already created the partition, you'll need to write an entry for it in /etc/fstab. See [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

