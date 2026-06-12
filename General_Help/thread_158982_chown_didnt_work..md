---
title: "chown didnt work."
date: 2006-04-12
forum: General Help
---

### Post by frup on 2006-04-12
i just did sudo chown -R username file

it didnt work went through the whole directory (about 40gb) and each said read only file. still cant access the folder
the folder is a ntfs mount. permissions say owner is root, group root... read only

i tried chmod too but that didnt work either.

how can i access these files? its the first time i've plugged this hdd in since i installed ubuntu... its my old windows xp drive from about 6 months ago

---

### Post by Sutekh on 2006-04-12
You can't chmod or chown Windows filesystems.  They aren 't compatible with Unix/POSIX permissions (those set by chmod)

You should follow this great tutorial on mounting Windows partitiosn

[http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

---

### Post by frup on 2006-04-12
okie dokie... i will try... when i tried linspire that did it all automatically :( havent plugged it in since then but just realised i need a few files i left on it

---

### Post by slug on 2006-04-12
Permissions and owner are set by the NTFS driver's options.

Take a look at [http://www.ubuntuforums.org/showthread.php?t=142481]("http://www.ubuntuforums.org/showthread.php?t=142481")  **3 - Edit the fstab file to mount the disks**

---

### Post by frup on 2006-04-12
[QUOTE=frup]okie dokie... i will try... when i tried linspire that did it all automatically :( havent plugged it in since then but just realised i need a few files i left on it[/QUOTE]

thank you very much appears to have worked great :D

---

