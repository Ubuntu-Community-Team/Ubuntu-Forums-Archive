---
title: "Unable to add second harddisk"
date: 2006-04-30
forum: General Help
---

### Post by aparsons on 2006-04-30
I recently installed Ubuntu ("server", no GUI).  I just bought a second harddrive and do not know how to get Ubuntu to recognize it.  What are the steps needed to take when adding a second harddrive?  I am using a SFF pc, and so I had to remove the CD ROM out of the bay to make room for the second harddrive.  Any help is GREATLY appreciated.

Thanks.

-Allan

---

### Post by Ramses de Norre on 2006-04-30
You need to mount and format it. I don't know how to format it from cli..
To mount it when you've formatted it you'll need to add an entry for it in /etc/fstab to define device, filesystem and mountpoint (which options you'll need depend on which filesystem it will be).

---

