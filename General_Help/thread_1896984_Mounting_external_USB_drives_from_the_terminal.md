---
title: "Mounting external USB drives from the terminal"
date: 2011-12-18
forum: General Help
---

### Post by LonelyStar on 2011-12-18
Hi,

I use the terminal as my "file manager". But what is annoying from the terminal is mounting external USB drives.
It is ok, that I have to type mount.
But what annoys me:
- Having to use sudo
- Having to find out if the usb drive is sd[a/b/c]
- Whenever I add a new external HD, I want to mount it into a directory with the name of the HD. So I have to create it using "sudo mkdir".

Is there a solution for the terminal avoiding these problems?

Thanks!
Nathan

---

### Post by mikewhatever on 2011-12-18
You could use 'udisks --mount device' instead of 'sudo mount device'. Check out 'man udisks' for more info.

---

