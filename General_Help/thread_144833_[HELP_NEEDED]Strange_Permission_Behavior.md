---
title: "[HELP NEEDED]Strange Permission Behavior"
date: 2006-03-15
forum: General Help
---

### Post by jasonli on 2006-03-15
Hi there,

When I copy a file from a cd rom to my harddisk home folder, the file takes a "locked" eblem with it. And If I copy a folder to the hard disk home folder, the folder itself is "locked", but the contents are not, so I can not add or delete files within the top parent folder, which is locked.

This is really strange, since when I check the permission properties of these "locked" file, it says that the file owner is ME!

Any of your precious help would be highly appreciated. Thank you very much!

:-k 

Jason

---

### Post by public_void on 2006-03-15
Change the permissions of the folder to read, write and execute. Because its a CD-ROM you don't have write permissions, which is true when you copy it to home.

---

### Post by jasonli on 2006-03-15
Thanks. But I think this is a quite silly bug, since if the source CD file is unwritable, why should the duplication on hard disk be unwritable too? Just copy the file will copy the same permission restriction is so uncomprehensible.

---

### Post by petervk on 2006-03-15
IMO this is a feature. Keeping the same permissions on a file when you copy it? Makes a lot of sense to me.

To fit it just go into the properties for the file and check the read, write, and execute permissions for yourself.

---

