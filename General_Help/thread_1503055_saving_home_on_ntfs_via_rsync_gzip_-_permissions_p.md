---
title: "saving /home on ntfs via rsync gzip - permissions preserved?"
date: 2010-06-06
forum: General Help
---

### Post by newboyo on 2010-06-06
Hi all,

I'm saving backups of my /home (via grsync using the options to preserve permissions and to compress) on a NTFS external drive.

I also plan to use mondo to save my / folder's iso to the NTFS. Will  that also be equally safe?

Is this safe i.e from the perspectives of preserving permissions for the files? I'd hate to have to partition the external into a ext3 FS to save my backups, coz it may muck up the backups of others from my family who've stored their backups on the same drive (different directories though)


rgds

---

### Post by Sin@Sin-Sacrifice on 2010-06-06
Make an image with dd first then compress it on the ntfs drive.

---

