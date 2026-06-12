---
title: "aMule: path for file download"
date: 2009-11-29
forum: General Help
---

### Post by lory on 2009-11-29
A gave aMule a new path with a new directory to store downloaded files (under preferences / difrectories), bit it is still downloading files to its aMule folder, which is a hidden folder.Looks like not accepting the new path...

---

### Post by Virtual Liberty on 2009-11-29
Haven't used it but as a workaround you could create a symlink and access the hidden folder from anywhere.

---

### Post by lory on 2009-11-29
good idea, how to do it?

---

### Post by Virtual Liberty on 2009-11-29
```
ln -s /home/user/.amule/downloads /home/user/amule-downloads
```

Change the first ( actual path to your files ) and second ( link ) path according to what folders and users you have there.

---

### Post by lory on 2009-11-29
It worked thanks

---

