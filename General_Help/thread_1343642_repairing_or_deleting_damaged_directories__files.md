---
title: "repairing or deleting damaged directories / files"
date: 2009-12-02
forum: General Help
---

### Post by yanvolking on 2009-12-02
Hello community,
 

 Does anyone know how to remove or repair a damaged/unreadable directory/file?
 

 during the copy operation of a tar file to my backup directory, the external HDD to which the copy operation was being performed was accidentally disconnected and now it is impossible to copy anything new to this directory or copy from.  It is also impossible to delete this directory : rm in Linux AND delete in windows don't work.  The error message states something to the effect that the directory is damaged or unreadable.
 

 I want to fix this by either repairing the directory or deleting it.
 

 Is there a specific command or procedure for doing this??

---

### Post by jbrown96 on 2009-12-02
You said you tried rm, but did you try to force it? ```
sudo rm -rf /FILES
```

---

