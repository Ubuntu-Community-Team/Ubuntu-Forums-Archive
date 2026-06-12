---
title: "LVM's - Will I lose them in a fresh install?"
date: 2011-04-30
forum: General Help
---

### Post by mr_luksom on 2011-04-30
I want to do a fresh install on my machine, however I use logical volumes for my user data (/home, documents, photos, movies, etc). The boot partition, including /etc, /var et al are all on a normal ext4 volume.

Will I lose my data managed by LVM? What do I have to do to prevent this?

---

### Post by mr_luksom on 2011-05-01
Turns out, no you don't.

You do have to reactivate them though, using:

```

vgchange -a y <volume_group_name_here>

```

Then you are free to mount them again.

---

