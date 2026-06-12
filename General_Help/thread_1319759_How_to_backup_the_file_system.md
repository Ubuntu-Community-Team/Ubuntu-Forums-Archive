---
title: "How to backup the file system?"
date: 2009-11-08
forum: General Help
---

### Post by viking_maniac on 2009-11-08
I've used Partition Image before on Ubuntu and Kubuntu (partimage) to backup the whole system, just in case, but now I use ext4 and have the system encrypted with LUKS, so I can't use partimage anymore. :(

Are there any other ways to backup my whole file system (root), and easily restore it when needed?

---

### Post by kio_http on 2009-11-08
just copy the contents to another partition:D!

---

### Post by cariboo on 2009-11-08
I copy all of /etc to my /home/<user> directory, then use rsync to backup /home to my file server. I don't bother backing up / as I already have all the configuration files backed up, and it is pretty trivial to do a reinstall.

---

