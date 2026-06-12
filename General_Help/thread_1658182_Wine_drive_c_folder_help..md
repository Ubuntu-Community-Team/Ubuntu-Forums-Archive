---
title: "Wine drive_c folder help."
date: 2011-01-02
forum: General Help
---

### Post by TDLShow on 2011-01-02
Hello and sorry if this is in the wrong place, but your help is always appreciated!

So I'm trying to move my mine Drive_C onto another harddrive and I seem to have alot more issues then I thought would be.

When I tried to move it manually like click and drag It would not move everything in that folder. Same when I tried with the terminal! 

Am I in way over my head! But thank you!

---

### Post by ajgreeny on 2011-01-02
Are you moving it so you can use it in another linux distro/operating system?

If you are, it is possible that there will be some ownership problems with the files and folders, unless you use the same username and the OS also uses the same guid for users as Ubuntu.  This can be overcome, but it is worth remembering.

Tell us more about why you want to do it, and how the disk you are copying to is formatted; fat32, ntfs, ext#, as that may be affecting the outcome.  I think you should be able to copy it if you start nautilus as root with ```
gksu nautilus
```but it would still be good to know why you are doing it.

---

