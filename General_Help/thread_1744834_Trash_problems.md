---
title: "Trash problems"
date: 2011-04-30
forum: General Help
---

### Post by PCaddicted on 2011-04-30
I moved a file to trash and the trash icon in the taskbar remained the same as when the trash is empty.If I put the pointer on it,I'll see "No items in Trash",but if I open the Trash,I'll see the deleted file(s).
How can I get it to work normally again?What may've caused the problem?

---

### Post by TheFirstMorningStar on 2011-05-04
I had the same problem in my old ubunto. I updated my ubunto to 11.04 and now I can not open the trash. When i try to open it, VCL gets open with an error. Any idea how I can resolve this?

---

### Post by DisturbedDragon on 2011-05-04
You probably deleted some files under root.  Use gksudo to launch your file manager and empty the trash that way.  Be extremely careful while using your file manager as root.

---

### Post by PCaddicted on 2011-05-06
I've managed to fix it.I used...
```
sudo apt-get update
```...,rebooted the computer and the Trash icon was OK again.
Thread marked as [SOLVED].

---

