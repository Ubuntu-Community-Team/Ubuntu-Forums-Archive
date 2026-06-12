---
title: "Samba file sharing multiple users same computer?"
date: 2010-07-28
forum: General Help
---

### Post by rlwpub on 2010-07-28
I setup samba file sharing to auto mount in fstab. Everything works great except when a computer has more than on user.

The folders in mnt are owned by root and ownership changes to the first user account no matter what user logs in. So only the first user can edit files in the mounted share.

Anyone got a clue why this is happening? Seems the mount folders should be changing ownership to the user that is logged in.

---

