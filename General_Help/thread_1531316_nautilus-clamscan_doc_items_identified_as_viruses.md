---
title: "nautilus-clamscan doc items identified as viruses"
date: 2010-07-14
forum: General Help
---

### Post by memphisrich on 2010-07-14
I found today that ClamTK identifies items in /usr/share/doc/nautilus-clamscan/examples folder as possible viruses. The four files in question, "clam.exe, clam.cab, clam.exe.bz2, and clam.zip" are all part of the standard file list in packages.ubuntu.com. None are marked as executable, but are identified as binary files by less. Any ideas why these files are here or what they do, besides generate false warnings?

---

### Post by WorMzy on 2010-07-14
Those are false-positives deliberately recognised as viruses (virii?) so that you can check that the scanner is detecting problematic files. You can safely delete them if you want to.

---

### Post by memphisrich on 2010-07-14
Thank you for the quick reply and good information. I didn't see anything in the readme's, but I may have overlooked it.

---

