---
title: "Copying Partitions to External Hard Drive"
date: 2010-01-09
forum: General Help
---

### Post by nyroshan on 2010-01-09
I'm going to be giving my brother an older laptop of mine, and before I do so I was wanting to copy all of the files from both the ubuntu and windows partition on my laptop to an external hard drive. I searched around and saw partimage, but rather than copy to an image file which wouldn't be easy to browse for files, i was hoping to have a backup that copies all the files while preserving the files directory structures. basically each of the partitions would be a folder on the external hard drive, like a copy/paste. Anyone recommend a particular program?

---

### Post by nyroshan on 2010-01-09
ttt

---

### Post by John Bean on 2010-01-09
> **nyroshan said:**
> i was hoping to have a backup that copies all the files while preserving the files directory structures. basically each of the partitions would be a folder on the external hard drive, like a copy/paste. Anyone recommend a particular program?

Erm... cp ;-)

Or, arguably better for this task, I'd use rsync - actually I'd use Grsync which is a nice friendly front-end GUI for rsync. It's in the repositories.

---

### Post by mkoehler on 2010-01-09
Yeah, if you're just looking to copy a whole partition, it doesn't get much easier than a recursive copy (cp).

---

