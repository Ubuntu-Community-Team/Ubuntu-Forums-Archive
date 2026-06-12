---
title: "Formatting an external hard drive."
date: 2010-12-16
forum: General Help
---

### Post by DylanRush on 2010-12-16
Okay, so I have this 1.5 terabyte external hard drive.  It has some bad sectors and although I keep reading that you can't really do much about them, I'm going to reformat the hard drive.  I was just wondering what utility would be best, or because it's NTFS and I need it to be NTFS afterwards, should I just do this on Windows?

---

### Post by efflandt on 2010-12-16
Since it has bad sectors and is NTFS, it would probably be best to format it from Windows, which will check for bad sectors during format.

However, drives reserve space to automatically transparently remap bad sectors to good sectors, so if you are actually seeing bad sectors, that is a bad sign that all error sectors are used up and things can only get worse.  So if it is under warranty, you should consider getting it replaced.  Or regardless, do not trust it for anything essential.

---

