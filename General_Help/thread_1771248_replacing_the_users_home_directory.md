---
title: "replacing the users home directory"
date: 2011-05-30
forum: General Help
---

### Post by uShafee on 2011-05-30
I have two partitions on my HD partition1 mount point / and partition2 mount point /home. I had ubuntu 11.04 32bit installed and  wanted to switch to 64bit so i reinstalled ubuntu and chose the same boot points. Since i reinstalled i had to create a new user and it created a new home folder. Now i want to replace my current users home folder with the previous home folder i had.

Would a simple rename work?

---

### Post by hwttdz on 2011-05-30
You can do a rename, but you'll need to adjust ownership of all files.  I'd do a copy and then a recursive find to change ownership of all files in the new directory.

---

### Post by uShafee on 2011-05-31
thanks. worked.

---

