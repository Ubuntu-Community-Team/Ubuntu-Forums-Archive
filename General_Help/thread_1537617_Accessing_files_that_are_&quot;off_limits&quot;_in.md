---
title: "Accessing files that are &quot;off limits&quot; in other partitions"
date: 2010-07-23
forum: General Help
---

### Post by Captain Hank on 2010-07-23
Greetings--

I've used Ubuntu for several years now, but it's my first post to these forums.  I'm in the process of recovering from a major, non-recoverable error with my OS.  I've managed to salvage the vast majority of my files by booting through a live CD and mounting the damaged partition in order to transfer my files to an external hard drive in preparation for a clean install of the OS.  However, I've encountered a problem accessing and copying certain files, with a dialog box informing me that "You do not have the permissions necessary to view the contents of "Folder Name."  Any tips on how to rectify this?

---

### Post by ubunterooster on 2010-07-23
```
gksu nautilus
```

---

### Post by Captain Hank on 2010-07-23
Thanks!

---

### Post by Captain Hank on 2010-07-23
Hmmm, It halfway worked.  I am now able to open and access the files, but when I try to copy them, an error box comes up with "The Folder 'name' cannot be handled because you do not have permissions to read it."

---

### Post by ubunterooster on 2010-07-23
right-click said file, select "properties" go to "permissions" and change them to "everyone"

---

### Post by Captain Hank on 2010-07-23
Worked perfectly.  Thanks, again!

---

### Post by ubunterooster on 2010-07-23
No problem. Glad (as always) to help. :D

---

