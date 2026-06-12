---
title: "Help with updating"
date: 2009-07-11
forum: General Help
---

### Post by trevongilpin on 2009-07-11
for some reason everytime i try to update or run a downloader (forgot what you call them) i get the following error message. 

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What do i have to do to fix it? i cant add/remove programs, I cant update my system, and i cant install gnomenu!

---

### Post by michy99 on 2009-07-11
Applications->Accessories->Terminal.

Enter this command:```
sudo dpkg --configure -a
```Enter your password. (you won't see it in the terminal.) Now run```
sudo apt-get update
```If you get errors, post them here.

---

### Post by trevongilpin on 2009-07-11
resolved. hopefully i will one day move past linux retardation.

---

