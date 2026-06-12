---
title: "Confused about changing file system set-up"
date: 2009-12-18
forum: General Help
---

### Post by gcday on 2009-12-18
I upgraded to 9.10 and have a slight problem - 

The system is a eee901 with a 4gb drive with the OS on and a 16gb drive with the (user)file system on - the only problem is that still has it's the (user) file system from the previous install on it (Documents, music, pictures etc). I have to manually mount it every time I want to access files on it or use it as drive space. Also 'documents', 'music', 'pictures', 'video' and 'downloads' for the current install are all on the 4gb drive but I want them to point towards and be on the 16gb drive. 

Hopefully people can understand what I'm on about... 

so.. how do I get the 16gb to automatically mount and how do I point "documents" etc to it?

---

### Post by yavoh on 2009-12-18
Adding the following lines to your /etc/fstab will automatically bind one folder to another at startup:

```
/path/to/source/folder /path/to/target/folder none bind 0 0
```This code will auto-mount non-root directory volumes at startup:

```
/device/path /folder/where/you/want/it filesystem defaults,error=remount-ro 0 2
```Make sure that "/device/path" is the actual device node of the partition you want-- you can find this in System->Administration->Disk Utility

Hope this helps :)

Since you want to bind your Documents folder (for example) to a mounted drive, make sure the mounting code (/device/path...) is in fstab BEFORE the "bind" code- otherwise it won't work.

---

