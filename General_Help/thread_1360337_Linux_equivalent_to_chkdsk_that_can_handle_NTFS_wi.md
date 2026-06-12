---
title: "Linux equivalent to chkdsk that can handle NTFS without data loss?"
date: 2009-12-20
forum: General Help
---

### Post by Nixie Pixel on 2009-12-20
Hello, I'm looking for a Linux equivalent to chkdsk to check a problematic Windows partition, without having to install yet another version of Windows to fix a computer that already has an Ubuntu partition on it. 

Unfortunately I've read that fsck has problems with NTFS and can cause data loss. Is there any alternative?

Thank you!

---

### Post by Leppie on 2009-12-20
you could try testdisk, have never tried it myself though.

---

### Post by lidex on 2009-12-20
Check these out:
[http://www.ubcd4win.com/contents.htm]("http://www.ubcd4win.com/contents.htm")

[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

---

### Post by dcstar on 2009-12-20
> **Nixie Pixel said:**
> Hello, I'm looking for a Linux equivalent to chkdsk to check a problematic Windows partition, without having to install yet another version of Windows to fix a computer that already has an Ubuntu partition on it. 

Unfortunately I've read that fsck has problems with NTFS and can cause data loss. Is there any alternative?

Thank you!

Install the **ntfsprogs** package and use the tool in that.

---

