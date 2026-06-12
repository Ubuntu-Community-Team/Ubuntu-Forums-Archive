---
title: "Can't copy files do to them being read only"
date: 2010-07-25
forum: General Help
---

### Post by wsfield99 on 2010-07-25
Hello,  I just upgraded to 10.4 from 9.4. In the past I was able to transfer MP3 files from my laptop to my usb thumb drive without any problems.  Now I receive a warning that the file I am trying to copy is read only.  I tried changing the permission via the properties tab but it did not work.  I have been able to copy files onto the computer, but when I attempt to copy them back I get the same error message.  I hope this is clear.  Thank you.

---

### Post by naknak987 on 2010-07-25
Open the terminal.
Type "gksudo nautilus" and press enter.
Navigate to the file, change its permissions, and close the window and the terminal. Then try it.

---

