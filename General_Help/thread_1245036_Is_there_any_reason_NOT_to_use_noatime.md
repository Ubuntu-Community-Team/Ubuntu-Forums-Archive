---
title: "Is there any reason NOT to use noatime?"
date: 2009-08-20
forum: General Help
---

### Post by biggerben on 2009-08-20
I hear performance can increase if you add noatime to the mount options. Is there any reason I would not want to do this?

---

### Post by Cheesemill on 2009-08-20
Using noatime stops the system from updating the 'last accessed' file attribute.
So if you need to know when a file was last accessed then don't use it.

---

### Post by Copernicus1234 on 2009-08-20
Seems to me that some applications will probably want to know this value, and its uncertain how they will react to it missing.

---

### Post by regala on 2009-08-20
> **Copernicus1234 said:**
> Seems to me that some applications will probably want to know this value, and its uncertain how they will react to it missing.

there's a relatime flag available (which is now default on ext3 and ext4 at least) since a few util-linux/kernel releases that updates access times only if they are older that modification times. Mutt, MUAs and MTAs could be willing such an option, noatime being a killer for any "new mail has arrived" kind of announcement.

---

### Post by Bachstelze on 2009-08-20
> **regala said:**
> Mutt, MUAs and MTAs could be willing such an option, noatime being a killer for any "new mail has arrived" kind of announcement.

Wrong. Mail programs don't use access times to check for new files...

---

### Post by regala on 2009-08-31
> **HymnToLife said:**
> Wrong. Mail programs don't use access times to check for new files...

stating wrong facts never helps a case, especially when no evidence's given.
so, I would say you're wrong:

[http://wiki.mutt.org/?MuttFaq/Folder](http://wiki.mutt.org/?MuttFaq/Folder)

especially, this:

> 
Why are "new" flags of mbox folders wrong in folder-list view?
As written in manual.txt, the flags are determined by comparing the timestamps of last access and modification. This can get messed up if the folders are "touched" by other programs than mutt, like "biff" or backup software.

There is also some issue with the "noatime" flag for mounting filesystems (most often used on laptops). If "noatime" is activated, no timestamp is updated for the last folder access, i.e. Mutt cannot determine if the folder has received new mail since last visited. For mutt before version 1.5.15, you can recompile it with the --enable-buffy-size option to "configure"; for mutt 1.5.15 or later see the $check_mbox_size option. Mutt will then use the folder size instead of the access times. (This is only a workaround and might give suboptimal results; another option is to use the MaildirFormat.) 


thanks a lot.

---

