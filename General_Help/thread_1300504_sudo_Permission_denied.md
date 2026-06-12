---
title: "sudo Permission denied"
date: 2009-10-25
forum: General Help
---

### Post by ha_60 on 2009-10-25
Hi Dear
when i type sudo I get this error
$ sudo
sudo: can't open /etc/sudoers: Permission denied

$ ls /etc/sudoers -la
-r--r----- 1 root root 557 2009-10-22 17:24 /etc/sudoers

I think it's for installing samsung unified driver (if I restart my system gdm will failed i tested it in previous linux) 

have any idea?

---

### Post by rockstarrem on 2009-10-25
Well, is your user in the sudoers file?

---

