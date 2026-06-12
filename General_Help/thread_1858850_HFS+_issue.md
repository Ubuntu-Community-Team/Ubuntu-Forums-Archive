---
title: "HFS+ issue"
date: 2011-10-13
forum: General Help
---

### Post by taunnt on 2011-10-13
Hello I have a HFS+ external drive that I have used with no issues. Now all of the sudden I can't write to it. What might have happened?. How can I see if journaling is still disabled to it. How would it get reset? It's kinda odd. I'm on Ubuntu 11.04.

Thanks

---

### Post by dcstar on 2011-10-13
> **taunnt said:**
> Hello I have a HFS+ external drive that I have used with no issues. Now all of the sudden I can't write to it. What might have happened?. How can I see if journaling is still disabled to it. How would it get reset? It's kinda odd. I'm on Ubuntu 11.04.

Thanks

Do a **fsck** on it.

---

### Post by taunnt on 2011-10-13
> **dcstar said:**
> Do a **fsck** on it.

That worked, thanks!

---

### Post by titusDT on 2011-10-29
Hi,

    I have an external drive with hfs+ journaling turned off. I would like to write to it from my Linux machine but I can't.

   the fsck command did not work in my case, it returns an error :confused:

gus

---

### Post by OrangeVixen on 2012-10-23
These are some of the things I learned with using any media with an HFS (Mac native) file system:

1. Make sure you create the file system using a Mac whenever possible, Ubuntu Linux can create it as well but I recommend using an actual Mac to create it.

2. Disable journaling.

3. Make sure the permissions are set to read/write for ALL users (which is not the default).

4. NEVER write to files at once on any HFS media under Linux.

5. Use an actual Mac's disk utility to check/fix any problem, not fsck on Ubuntu Linux (except as a last resort).

---

