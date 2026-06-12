---
title: "Wiping out hard drives: Kill Disk or other method?"
date: 2009-08-02
forum: General Help
---

### Post by Sef on 2009-08-02
I have some external hard disks that I want to wipe clean, but I have some questions:

1) Is KillDisk easy to use?

2) From a command in Terminal?

3) Is there another way or other software?  (DBan does **not** delete external hard drives.)

---

### Post by realzippy on 2009-08-02
DiscDump (DD) could do the job,e.g.:

dd if=/dev/urandom of=/dev/hda  

"/dev/hda " of course depending on your drive..

---

### Post by indytim on 2009-08-02
Just do a low level format.  Seagate used to offer disc tools that included a low level format.  

IndyTim

---

### Post by scouser73 on 2009-08-02
> **Sef said:**
> I have some external hard disks that I want to wipe clean, but I have some questions:

1) Is KillDisk easy to use?

2) From a command in Terminal?

3) Is there another way or other software?  (DBan does **not** delete external hard drives.)

Try the information here: [http://ubuntuforums.org/showthread.php?t=395937]("http://ubuntuforums.org/showthread.php?t=395937").

---

