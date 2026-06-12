---
title: "Offline CD/DVD Archival with symlinks"
date: 2011-06-22
forum: General Help
---

### Post by byb3 on 2011-06-22
Hello,

I was wondering if there was a way, to add a folder to a hard disk which was full of symlinks to a CD drive.

This would primarily be a way to store offline media and a way to access it.  I would still be able to browse the folder structure and see the files (but possibly not the sizes).  I imagine something like this:

/archive/cd/cd1/photos/me.jpg > /mnt/cdrom/cd1/photos/me.jpg

Therefore I can see what files I have available, and I know which media to insert (in this case cd1) and I would then be able to view the files?

Or if anyone has a better idea I'm open to it.  Just to mention I don't have a GUI on this server, it is completely headless so any solution needs to be console based :)

Regards,

---

### Post by byb3 on 2011-06-22
It seems I've just found it:

cp -Rs /mnt/cdrom/* /home/archive/cd1/

I'm not sure if this will work after a restart and it needs further testing, but the idea is there :)

---

