---
title: "NTFS Partition in external drive."
date: 2010-02-14
forum: General Help
---

### Post by themarker0 on 2010-02-14
It doens't show. I have a couple things that may factor into it


[LIST]
[*]I fudged it up
[*]I have it through a usb extender
[*]I also use it on windows
[/LIST]

Thank you for you help in advanced.

---

### Post by flippo on 2010-02-14
The 2nd and 3rd issue shouldn't be a problem, the first is rather vague though.  What is the output of ```
fdisk -l
```

---

### Post by themarker0 on 2010-02-14
Empty. It doesn't see it coming up.

By i fudged it up, i mean it thinks it has the wrong artictecture. I have to format and fix one of these days, but i haven't the time.

---

### Post by flippo on 2010-02-14
did you "fdisk -l" or "sudo fdisk -l" I forgot to put in the sudo, but it is required.

---

### Post by themarker0 on 2010-02-14
That would be it. It sees it.

---

### Post by flippo on 2010-02-14
okay, can you mount it?```
sudo mount <device> <mountdir>
```

---

### Post by themarker0 on 2010-02-14
Doesn't show. :S

---

### Post by flippo on 2010-02-14
if you open a terminal and type:```
nautilus <mountdir>
``` Where <mountdir> is the directory you mounted the device to, is it populated with the files in the drive?  If so, I can help you get it set up correctly.

---

### Post by themarker0 on 2010-02-14
Aha! Thank you very much good sir.

---

