---
title: "Pointing folders (documents, music, etc) to another location"
date: 2011-04-03
forum: General Help
---

### Post by BKbroila on 2011-04-03
I've got a shared drive that's in a readable and writable format (I think FAT32). Sorry I forgot the exact format, but it's readable and writable from both Ubuntu and Win7, so no worries

Anyways, I'd like to have Documents on Ubuntu be able to point to a folder in that shared drive. How do I do this? I've tried googling, but came upon suggestions using Nautilus, but it seems to be for older versions of Ubuntu

Thanks

---

### Post by fela on 2011-04-03
Assuming there isn't an existing documents folder inside your home folder (if there is, delete it), and the documents folder you want to point to is at /media/disk/Documents, do this:

```
cd /home/$USER
ln -s /media/disk/Documents
```

Now you should have a folder in your home folder called Documents, that is a link to Documents in /media/disk.

---

