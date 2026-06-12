---
title: "Copy Home directory to USB flashdrive"
date: 2012-09-24
forum: General Help
---

### Post by bertold on 2012-09-24
Running Ubuntu 10.10 on Acer Netbook ZX5. Eventually realized that drag and drop file manipulation doesn't work on 10.10.
Considered upgrading to 12.04, but reluctant because of brightness control problem with 12.04. Ended up installing PCManFM file manager version 0.9.7, which did allow me to drag and drop.
However, when I attempted to copy the /home directory to a 32 Gig USB flashdrive (formatted to ext3), it seemed to do so, but there were error messages, and the files did not appear on the flashdrive. I assume the problem lies with permissions.
How to do this?

---

### Post by shreepads on 2012-09-24
What were the error messages?

---

### Post by NCLI on 2012-09-24
First of all, drag-and-drop should work just fine.

More importantly though; what error messages?

---

### Post by C.S.Cameron on 2012-09-24
Use **rsync** to copy home folder.

---

### Post by dcstar on 2012-09-25
> **bertold said:**
> Running Ubuntu 10.10 on Acer Netbook ZX5. Eventually realized that drag and drop file manipulation doesn't work on 10.10.
Considered upgrading to 12.04, but reluctant because of brightness control problem with 12.04. Ended up installing PCManFM file manager version 0.9.7, which did allow me to drag and drop.
However, when I attempted to copy the /home directory to a 32 Gig USB flashdrive (formatted to ext3), it seemed to do so, but there were error messages, and the files did not appear on the flashdrive. I assume the problem lies with permissions.
How to do this?

/home is a system folder that only system admin (using sudo) accounts have full access to. The user folders under /home are only fully accessible by the user accounts that own them.

Either run Nautilus with root privileges or just copy your own /home folder.

---

