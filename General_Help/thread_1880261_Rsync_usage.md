---
title: "Rsync usage"
date: 2011-11-13
forum: General Help
---

### Post by Bardwise on 2011-11-13
I used to use freefilesync to back up my files but no longer want to, so I'm going to use rsync instead.

I want to mirror one folder to another, only copying over updated files.

Can somebody please confirm the rsync command that I would use in this circumstance?  I'm just wary of losing 150 GB worth of stuff.

---

### Post by herta on 2011-11-13
Assuming your backing up to another disk connected to the same computer:

  rsync -aH source-directory/* target-directory/

will do the trick.  Run it from the root account if the directories contain files owned by more than one account. 

If you want a list of which files are being copied, add '-v'.
If you also want to cleanup files which have been removed from your source-directory, add '--delete'.

The man pages are pretty clear if you want to investigate further.

Oh, and since you are talking 150 GB, depending on how fast your hw is, it will take a while before you see anything appear in the target-directory, because rsync will build a list of what it needs to copy before actually starting.

It's a good tool.  We use it at work to keep many of our disaster recovery servers is sync - and yes, we do run DR tests.

Kind regards,

Herta

---

