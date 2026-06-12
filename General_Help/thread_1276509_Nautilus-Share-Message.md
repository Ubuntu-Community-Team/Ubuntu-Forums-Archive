---
title: "Nautilus-Share-Message"
date: 2009-09-27
forum: General Help
---

### Post by saroo on 2009-09-27
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:5409): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///root

(nautilus:5409): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:5409): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time

---

### Post by swerdna on 2009-09-28
Check if you have installed the package nautilus-share which is available in e.g. Syanaptic in System --> administration --> synaptic --> nautilus-share

Then if you have installed it, there's a deeper problem and you'll have to configure "usershares" further, as discussed completely in this thread: [http://ubuntuforums.org/showthread.php?p=7972299](http://ubuntuforums.org/showthread.php?p=7972299)

---

