---
title: "how to erase memory for 9.04 when sudo apt-get clean don't work"
date: 2010-05-07
forum: General Help
---

### Post by Skipopis on 2010-05-07
I just got 9.04 running on my com and I can't upload updates it says to run sudo apt-get clean but it does nothing... please help

---

### Post by kellemes on 2010-05-07
> **Skipopis said:**
> I just got 9.04 running on my com and I can't upload updates it says to run sudo apt-get clean but it does nothing... please help

*sudo apt-get clean* only cleans the apt-cache (afaik).
You have a diskspace problem maybe?

Anyway.. open a terminal-window and start typing..
```
sudo apt-get update
```
You get any errormessages?

---

### Post by _0R10N on 2010-05-07
I don't get it, you want to upload updates, or download them?

---

### Post by Lightstar on 2010-05-07
I think he wants to clear the ram memory?

if you want to clean your computer, there's "sudo apt-get autoremove" that removes unneeded packages.

---

### Post by Skipopis on 2010-05-07
no error messages when I run sudo apt-get update

---

### Post by Skipopis on 2010-05-07
download updates sorry for the confusion

---

### Post by Skipopis on 2010-05-07
I'll explain again: I'm trying get updates from update manager and it says "the upgrade needs a total of 498M free space on disk '/'. Please free at least an additional 495M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'." I ran sudo  apt-get clean n it did nothing. please help

---

### Post by Skipopis on 2010-05-07
and I checked the trash nothing is in it.

---

