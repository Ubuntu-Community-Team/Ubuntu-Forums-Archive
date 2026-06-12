---
title: "Do not see Windows partition on Ubuntu 11.10"
date: 2012-03-02
forum: General Help
---

### Post by yonyz on 2012-03-02
Hello,

When I ran 11.10 through the disc, without installing it, I saw the Windows partition fine. Now that I've installed 11.10, through the Windows installer, I do not see the Windows partition and cannot access pretty much all my files. 

How can this be solved?

---

### Post by oldfred on 2012-03-02
Did you do a wubi install? That  is inside the Windows NTFS partition, and boots with the Windows boot loader.

If so the Windows files are in /host in the Nautilus browser.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by yonyz on 2012-03-02
Thanks!

---

