---
title: "Need Help Moving a File"
date: 2009-07-05
forum: General Help
---

### Post by robertqadkins on 2009-07-05
Okay, I have a file stored on my Desktop. I need to move this file to a jump drive. The only problem is that i can't boot into ubuntu and can only use recovery mode. Can anyone help?

---

### Post by taurus on 2009-07-05
Is your thumbdrive mounted?  You can just use the cp (for copy) command to copy it from your ~/Desktop to the thumbdrive.  

Assuming your login name is robert and your thumbdrive is mounted to /media/disk, you could do something like

```
cp /home/robert/Desktop/**filename** /media/disk
umount /media/disk
```
_Make sure_ you unmount the thumbdrive first before you unplug it.

---

