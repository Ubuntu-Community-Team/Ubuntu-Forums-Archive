---
title: "What Backup Software for Ubuntu?"
date: 2009-07-28
forum: General Help
---

### Post by griffo69 on 2009-07-28
What is everyone using?
And will it backup my virtual stuff I am using on the Ubuntu Host?:)

---

### Post by niteshifter on 2009-07-28
Hi,

Whatever they please ;)

Some use dd.
Some use tar - they are a remarkably patient lot. tar is  s l o w  on multi-GB backups.
Some use sbackup, based on tar so same as above.
Some swear by clonezilla.
Some like partimage.
Some like mondo-rescue.
Some use rsync.
Some like remastersys.

There's more, but you get the idea and some programs to check out. There's no such thing as a one-size-fits-all backup solution. Myself, I use partimage (run from System Rescue CD on a USB stick) for monthly full backup, rsync daily on my home folder, with a few simple scripts to track packages downloaded in between full backups.

---

### Post by philcamlin on 2009-07-28
remastersys is really good

---

