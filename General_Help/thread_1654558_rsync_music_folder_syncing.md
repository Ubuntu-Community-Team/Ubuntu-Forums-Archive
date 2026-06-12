---
title: "rsync music folder syncing"
date: 2010-12-28
forum: General Help
---

### Post by neonl on 2010-12-28
Hey

Imagine this situation:
[LIST]
[*]Big music folder in my desktop's hard drive. Ext4 (Linux). This directory has a typical "Artist/Album" directory structure and is constantly being updated (cd rips, downloads, etc.);
[*]I have an NTFS 2.5" external hard drive;
[*]Basically, music is never 'updated' in the exernal hard drive, but I want to be able to run a script which, when it is executed, copies all 'new music' in the from the desktop to the external HDD. This is supposed to be done periodically.
[*]This doesn't seem impossible, but I don't know much about this rsync/bash scripting stuff, so I found [this old HOWTO thread]("http://ubuntuforums.org/showthread.php?t=820425&highlight=rsync+folder"), but it says that it only copies 'COMPLETE hard drive to EXT/NTFS (minus massive music folder)'.
[/LIST]
What is the problem exactly?

---

### Post by dcstar on 2010-12-28
> **neonl said:**
> 
.....
Basically, music is never 'updated' in the exernal hard drive, but I want to be able to run a script which, when it is executed, copies all 'new music' in the from the desktop to the external HDD. This is supposed to be done periodically.
.........

Use Unison.

---

