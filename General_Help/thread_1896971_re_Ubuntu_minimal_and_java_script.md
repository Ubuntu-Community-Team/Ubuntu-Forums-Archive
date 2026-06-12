---
title: "re Ubuntu minimal and java script"
date: 2011-12-18
forum: General Help
---

### Post by rng on 2011-12-18
I want to install a minimal system which should boot into text mode and straight run a script (as root) which mounts 2 partitions (one of which is ntfs) and runs a java (text) program (which involves reading and writing files on 2 partitions) and then powers off. 

Can I use ubuntu minimal for this and how do I install java and ntfs-3g there? For the startup script, can I put command in rc.local?

---

### Post by mikewhatever on 2011-12-18
/etc/rc.local is a good place to put commands that need to be run as root.

To install java and ntfs-3g:

```
sudo apt-get install icedtea-6-jre-jamvm ntfs-3g
```.

---

