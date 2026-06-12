---
title: "sync on USB disk"
date: 2006-06-08
forum: General Help
---

### Post by calutateo on 2006-06-08
Dear all,

I have an external USB disk I use for backups. And I am only able to copy some files (lets say 30 MB or so) to the disk. Then the copying process just freezes.
This happens while using each of the following three tools: GUI (Nautilus), the cp command or rsync
I suppose that the data to copy is loaded into RAM memory until there is no space left, so it has to be written to the disk by mean of the sync() function.

I tried executing the sync command but it does nothing but blocking the shell.

Any suggestions?

Regards, Carsten

---

