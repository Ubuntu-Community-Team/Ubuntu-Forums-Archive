---
title: "F-Spot Backups (how) and Universal Tags"
date: 2010-11-26
forum: General Help
---

### Post by onaridge on 2010-11-26
I have started tagging 10 years plus worth of photos and am using F-Spot. What is the easiest way to back up F-spot so that if I have to reinstall on a failed system I can have the album plus tags exactly as they were after I install the F-Spot program again. 

Is there some kind of simple incremental backup I can set up or do I just have to backup, say weekly, the entire folder/s?

Since the tags are embedded in the actual photos, does this man that they will be retrievable in just about any photo program on any OS?

I don't want to spend weeks tagging photos unless I am reasonably sure I can back things up and use the tags 10 years later on either a Linux or another OS.

---

### Post by aeiah on 2010-11-26
if the tags are in the photos (which if not the default, is certainly an option with f-spot) then you can back up the photos as you would any other file.

to be able to read the tags though, you'd need a photo mananger that was aware of them. i believe new versions of shotwell can read/store tags to the photos themselves as well as f-spot. i dont know about any other one because ive never had need to look, but obviously the folder structure should be retained if this is how the photos are actually saved so even if you view them with some pokey windows photo manager, you should still be able to have the directory structure. the tags might not be viewable, but since they're in each photo, they'll still exist.

my photos are backed up using backintime, which really just uses hard linking (see 'cp -al') and rsync to do incremental backups. it only copies the files that have changed (and hard links the rest from a previous backup) 

you should be aware that if you add a new tag to every one of your photos, then every photo will have changed (since you aren't using a database) and so if you do this regularly your incremental backups will be quite large.

---

### Post by onaridge on 2010-11-26
Yes I selected the embedded feature for the tags.

So do I just back up the "Pictures" folder with BackInTime then? 

If I ever to have reinstall Ubuntu or an upgrade goes bad I can simply copy the Pictures folder into the default pictures folder then, correct?

---

