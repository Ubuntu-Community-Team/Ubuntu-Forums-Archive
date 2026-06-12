---
title: "Turned my WD Passport into a drag n' drop flash drive - how to do &quot;quick update&quot;?"
date: 2009-06-28
forum: General Help
---

### Post by PsychedelicWonders on 2009-06-28
Ok I didnt like the Passport software and heard bad things about it.

So I formated it to a NTFS style and basically turned it into a 500g flash drive.

Now I've already transfer/copied the HDD I wanted to back up.

Now some new things have been added/deleted.

So how do I update my Passport to reflect all of the new files/old ones via a drag n drop?

I dont want to have to re-copy all of the files again just to get to the new stuff.

---

### Post by Dysport on 2009-06-28
I don't know about a "drag-and-drop" solution, but the terminal command *rsync* might be what you are looking for.

```
rsync -r <source> <target> 
```

---

### Post by PsychedelicWonders on 2009-06-28
Hmm.  I should have stated that I'll be doing this in windows.

I'm doing this in order to move my Ubuntu partition. 

Any solutions for a windows quick update drag n drop?

---

### Post by Dysport on 2009-06-28
Very well then, you could run Cygwin with rsync. Or how about trying [cwRsync]("http://www.samba.org/rsync/download.html")? Would that be an acceptable solution?

Back in my windows days I used Acronis TrueImage Home as it allows incremental backups, but I guess that's not what you need right now.

EDIT: [This]("http://winrsync.sunsite.dk/") looks interesting as well.

---

