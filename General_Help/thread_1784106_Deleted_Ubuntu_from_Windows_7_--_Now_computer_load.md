---
title: "Deleted Ubuntu from Windows 7 -- Now computer loads white screen"
date: 2011-06-16
forum: General Help
---

### Post by lopez33 on 2011-06-16
Hello,

I was running Windows  7 and Ubuntu 10.4 and 11.04 Dual Boot. I decided to delete the Ubuntu partitions and restore my computer's hard drive to entirety for Windows 7 through the partition manager. Once I did that and successfully restored it,** I restarted my computer and once it loads the acer screen it goes into a white screen and then restarts. **

I appreciate any help.

---

### Post by coldraven on 2011-06-16
I don't understand the white screen business, that sounds bad :(
You could try booting from a Windows recovery disk and see if bootrec.exe can find your system. Usually at the windows command prompt you would type ```
bootrec.exe /fixmbr
```but read up on the Microsoft website first.

---

