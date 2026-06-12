---
title: "Synchronize Documents"
date: 2010-04-21
forum: General Help
---

### Post by arashiko28 on 2010-04-21
Can I synchronize documents between a folder and my USB drive?
I have been moving between 2 computers and working my docs on both, my laptop and the other computer on my USB drive, is there a way that I can synchronize the documents updated between both my USB and laptop?

---

### Post by lovinglinux on 2010-04-21
[rsync](apt:rsync)

---

### Post by egalvan on 2010-04-21
unison works well to synchronize files.

It's in the repos.

---

### Post by arashiko28 on 2010-04-26
> **egalvan said:**
> unison works well to synchronize files.

It's in the repos.

Thanks works like a charm!

---

### Post by alienprdkt on 2010-05-10
Is there a way with Unison to setup to sync more then one root path? 

and more then one source path?

Wanted to set something up like this...

Mount smb shares to local server:
                             /mymounts/server001/source
                             /mymounts/server002/source

then I would like to sync those mounted directories to something like this:

sync to directories:
             /syncs/server001/source
             /syncs/server002/source

can this be done?

can you please explain how I would configure this?
Thanks in advance

---

