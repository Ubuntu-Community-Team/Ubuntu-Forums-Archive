---
title: "Ktorrent &quot;source and destination are the same file.&quot;"
date: 2010-01-24
forum: General Help
---

### Post by Weidbrewer on 2010-01-24
I'm using Ubuntu 64 8.10, and recently I've been getting an error in Ktorrent where, when the file finishes downloading I get a message that says "source and destination are the same file" and then the file disappears.  Anyone have any ideas?

---

### Post by lovinglinux on 2010-01-24
In Ktorrent preferences, make sure the "Default save location" and "Move completed downloads to" are not the same. It looks like it is trying to move the downloaded files once completed, but since the destination and source location are the same, the file gets screwed.

If that is not the case, then disable "Move completed downloads to", so Ktorrent keeps the downloaded file in place.

---

### Post by Weidbrewer on 2010-01-25
That seems to have done the trick.  I changed the directory for DLs, and haven't had any problems since.  Thanks!

---

