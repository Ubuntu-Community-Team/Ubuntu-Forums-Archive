---
title: "Is this a legitimate way to backup and restore your system?"
date: 2006-06-25
forum: General Help
---

### Post by escape on 2006-06-25
This just popped in to my head, I'm wondering if it will work. The goal is to basically make an extremely small fingerprint of your current ubuntu installation, that can be used to restore everything to how you had it:
1. Make a giant tarball of /home/yourusername
2. ```
dpkg -l > pkglist.txt
```
3. Run sed/tr on pkglist.txt so that everything is on one line
4. Save the tgz, pgklist.txt, and /etc/apt/sources.list externally, and reinstall ubuntu
5. Use your same username when reinstalling.
6. Once reinstalled, copy your old /etc/apt/sources.list over the new one.
7. Run ```
sudo apt-get update
sudo apt-get install `cat pgklist.txt`
```8. Reboot into single-user mode. Copy your old home directory over your new one. Reboot again normally.

What do you think? This can be expanded by backing up everyone's home directory, I think. I may try it pretty soon...

---

### Post by aysiu on 2006-06-25
Only way to know for sure is to test it.

Small fingerprints aren't important to me, so I prefer to just .tar my documents and pictures and music and occasionally back up my entire partition image.

---

### Post by escape on 2006-06-25
Well, I guess I'll let everyone know when I do it. :)

---

