---
title: "permissions and owners are messed up in /usr"
date: 2009-10-30
forum: General Help
---

### Post by x3roconf on 2009-10-30
I chowned some subfolders in /usr accidentally to root:root (chown -R) and for example sudo is not working anymore because of lacking setuid rights. Should I make a complete re-install or is there a way to restore correct permissions and owners for /usr and it's subfolders?

---

### Post by x3roconf on 2009-10-30
Anyone?

---

### Post by lilbill on 2009-10-30
You should be able to boot into 'recovery mode' if using GRUB boot loader.  If possible, do that then choose 'drop to root shell' or root prompt to take you to a root command line where you will be able to fix the ownership.

---

