---
title: "the destination is read-only in ubuntu 11.10"
date: 2011-10-17
forum: General Help
---

### Post by Kvas4 on 2011-10-17
I just upgraded to Oneiric 11.10 and noticed that every time I either copy or move files from Ubuntu to Windows7 I have on the other part of my hard drive or to any external drive I have attached, I get this message "the destination is read-only". Being a root, tried to give either permission or even to share those drives, didn't work! Got the same error message :"Read-only system". Any suggestions? Thanks in advance!

---

### Post by manustays on 2011-10-17
I got the same problem in my Ubuntu 10.10 install!! External NTFS partitions are read-only even from the root! Guess something to do with the NTFS driver being used by default

---

### Post by Kvas4 on 2011-10-17
...did you do anything about it?

---

### Post by Kvas4 on 2011-10-17
I checked all the threads with similar issues! None of them have helped! Anybody, who can figure it out?

---

### Post by effenberg0x0 on 2011-10-17
[http://mygeekopinions.blogspot.com/2011/06/how-to-install-ntfs-config-in-ubuntu.html](http://mygeekopinions.blogspot.com/2011/06/how-to-install-ntfs-config-in-ubuntu.html)

---

### Post by Ch4rg3D on 2011-10-18
> **effenberg0x0 said:**
> [http://mygeekopinions.blogspot.com/2011/06/how-to-install-ntfs-config-in-ubuntu.html](http://mygeekopinions.blogspot.com/2011/06/how-to-install-ntfs-config-in-ubuntu.html)

Worked like a charm. Thank you!

---

### Post by ducky12432 on 2011-10-23
> **Kvas4 said:**
> I just upgraded to Oneiric 11.10 and noticed that every time I either copy or move files from Ubuntu to Windows7 I have on the other part of my hard drive or to any external drive I have attached, I get this message "the destination is read-only". Being a root, tried to give either permission or even to share those drives, didn't work! Got the same error message :"Read-only system". Any suggestions? Thanks in advance!

this is because ntfs-3g is not installed by default anymore.

install ntfs-3g and you will be able to read/write to ntfs partitions again.

---

