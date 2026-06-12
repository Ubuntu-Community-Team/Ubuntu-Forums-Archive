---
title: "file operations is buggy"
date: 2010-09-03
forum: General Help
---

### Post by UncleMonty on 2010-09-03
Whenever I move files from a USB memory stick or external hard drive or any other such device the file only seems to transfer 99% of the data and often during moving file operations will freeze and an offer of 'force quit' will come up (although file operations will eventually vanish with the 99% of the file being moved).

Can anything be done to rectify problems with file operations?

---

### Post by VanillaMozilla on 2010-09-03
I have no idea how you can hurry it up, but when you remove media, right click on it and select "Eject", then wait until the icon disappears.  That will allow the system to clean up properly.  It's also possible you have a bad device.

---

### Post by Austin25 on 2010-09-03
You could try the command, "cp"

---

### Post by UncleMonty on 2010-09-03
> **Austin25 said:**
> You could try the command, "cp"

What does that do?

---

### Post by hakermania on 2010-09-03
open up the terminal and do
cp (file you want) /media/My_USB_Device

---

### Post by dtfinch on 2010-09-03
I've had that happen with large network copies as well (just last week on 10.04, fully updated). It was actually done copying (a couple thousand files, maybe 1.8gb), but the copy dialog was stuck at 99%, and nautilus was taking 100% cpu. I left it for several more minutes, much longer than the first 99% took, and nothing changed, so I eventually just killed the process.

---

