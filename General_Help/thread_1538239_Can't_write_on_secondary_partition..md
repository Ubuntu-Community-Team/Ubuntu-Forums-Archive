---
title: "Can't write on secondary partition."
date: 2010-07-24
forum: General Help
---

### Post by Punkristo on 2010-07-24
I have a second 8GB partition but for some reason I cant write in it at all. I formated it but still doesn't let me write in it. I tried doing this:

> sudo chown -R username:username /media/BT

But this is what I get:

> chown: changing ownership of `/media/sda2/FOUND.000/FILE0000.CHK': Operation not permitted
chown: changing ownership of `/media/sda2/FOUND.000': Operation not permitted
chown: changing ownership of `/media/sda2': Operation not permitted

---

### Post by ubunterooster on 2010-07-24
try running ```
gksu nautilus
``` and go to that drive and right-click on it and select "permissions". Change ownership to your username

---

### Post by Punkristo on 2010-07-24
I'm getting this error when I select my username

> The owner could not be changed.

Sorry, could not change the owner of "sda2": Error setting owner: Operation not permitted

---

### Post by gabak on 2011-09-27
are you trying to do that in ext3 or ext4 file system?
it looks like you are doing that on ntfs and that is nt possible i guess in windows Filesystems

---

