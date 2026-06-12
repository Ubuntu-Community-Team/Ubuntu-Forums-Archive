---
title: "Deleted Account/Home Folder... Possible to Undelete?"
date: 2011-05-21
forum: General Help
---

### Post by kjkoec on 2011-05-21
Just recently I made a separate user account for "guests" to show off some lmms creations.   At the time, I thought I copied and pasted lmms' working dir. into the new "guest" home folder.  I had really CUT and pasted it, however, but before I realized, I'd already deleted the "Guest" account.

](*,)

This is months of project files... gone.
Is there any program out there that could possibly restore lmms' .mmpz (project) or .xpf (preset) files?  I believe both are actually .xml's in reality.  I shut down Ubu shortly after it happened to help prevent overwriting and just tried photorec in Ubuntu Rescue Remix, but the program honestly isn't the most intuitive I've come across.

Any information regarding recovery (or the impossibility) would be appreciated.  Even if nothing can be done, I'd like to know so as to get started recreating...

---

### Post by linuxinstalledfromhdd on 2011-05-21
[http://cinderbox.net/2011/05/12/photorec-digital-picture-and-file-recovery/](http://cinderbox.net/2011/05/12/photorec-digital-picture-and-file-recovery/)

---

### Post by kjkoec on 2011-05-21
Thanks for the quick reply.  Your link proved I wasn't working photorec correctly, but will it recognize the mmpz's or xpf's?  They aren't on the list of known file types, but xml is.  I will try it anyway.

EDIT: grep'd through 4 gb of what photorec turned up and no mmpz's or the like... only some mentions of it.

---

### Post by kjkoec on 2011-05-21
Tried Extundelete on entire /home/guest dir:

```
ubuntu@ubuntu:~/Downloads/extundelete-0.2.0$ sudo extundelete /dev/sda5 --restore-directory /home/guest
WARNING: Extended attributes are not restored.
Loading filesystem metadata ... 597 groups loaded.
Loading journal descriptors ... 30407 descriptors loaded.
Writing output to directory RECOVERED_FILES/
Searching for recoverable inodes in directory /home/guest ... 
3188 recoverable inodes found.
Looking through the directory structure for deleted files ... 
3188 recoverable inodes still lost.
No files were undeleted.
```

**However, trying Extundelete on entire /home/guest/lmms WORKED.**
All projects, most presets back.

---

