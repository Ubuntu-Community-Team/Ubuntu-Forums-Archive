---
title: "Bash and spaces in folder names?"
date: 2009-12-25
forum: General Help
---

### Post by ostraaten on 2009-12-25
Hi,
Is there a way to use folder names with spaces in bash?

I'm trying to backup to an USB drive that mounts as a folder with spaces in it. The name came with the drive.

Now I notice that bash won't recognize such folders/paths. I have tried several things: escape characters, quotes etc. Message is always the same: no such file or directory.

I googled for a solution but that didn't help. It seems really not possible to use folders names with spaces. Is there a workaround of some sort? 

Kinda hard to believe this is so hard to do with Linux/Ubuntu/Bash?

Thanks and Regards,
Onno[LEFT][LEFT][/LEFT][/LEFT]

---

### Post by Leppie on 2009-12-25
you'll have to put a backslash before the space. for example "Documents and Settings" would become "Documents\ and\ Settings".

changing the label of the pen drive will also change it's mount point (change it to something without spaces ;))

---

### Post by ghostdog74 on 2009-12-25
just put double quotes (or single quotes) around your file name.

---

