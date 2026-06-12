---
title: "Password Protected .doc File; Only Opens as Read Only"
date: 2010-11-30
forum: General Help
---

### Post by manco on 2010-11-30
I created a password-protected .doc file in Windows yesterday using the latest version of OpenOffice (3.2.1)

Opening the file worked perfectly; double-clicked the file, OpenOffice popped up and prompted me for the password, then it let me edit the document as usual.

Tried it on another computer with Microsoft Word; worked perfectly as well.

For some reason though, it won't work in Ubuntu (10.10).  I'll double-click the file, it'll open with OpenOffice and prompt me for the password, but once it opens it's in "Read Only" mode.

I tried it on **another** Windows computer, just to see if it would work, and it did.

I right-clicked the .doc file and looked at the permissions: (picture edited for privacy)

[IMG]http://i56.photobucket.com/albums/g198/yellowsnow4free/Computer%20Stuff/Permissions.png[/IMG]

Every time I tried changing it from "Read-only" to "Read and write" it automatically (and immediately) switched back to "Read-only"

Does anyone know how to fix this?

Thanks

---

### Post by efflandt on 2010-11-30
Who do you want to be able to open and edit the file?  The dialog you show shows "Read and write" for owner.  Or are you a different user when trying to open/edit the file?  Only the owner (or root) would have permission to change that.

If the file is "Read only" for group and other, they can read it or copy it, and save it under a different name, but they cannot overwrite the existing file without write permission.

---

### Post by manco on 2010-11-30
"yellowsnow4free" (me) is the owner.

I'm the owner of the document, but for some reason I can't change it to "Read and Write"

---

### Post by BrandonC19 on 2010-11-30
Try a ```
sudo chmod 777
``` on it and see if that does it.

---

### Post by manco on 2010-11-30
> **BrandonC19 said:**
> Try a ```
sudo chmod 777
``` on it and see if that does it.
How do I do that **on it**?

I'm decent with Ubuntu but stuck when it comes to more complicated Terminal commands

---

### Post by killa.fr0gg on 2010-11-30
sudo chmod 777 /path/to/document

For example, if the document is in your Documents folder, type:

sudo chmod 777 /home/YOURUSERNAME/Documents/filename.fileextension

Note that the command line is case sensitive. Try that and get back to us.

BTW: Terminal is located at the main menu Applications->Accessories->Terminal

Good luck!

---

### Post by manco on 2010-12-01
> **killa.fr0gg said:**
> sudo chmod 777 /path/to/document

For example, if the document is in your Documents folder, type:

sudo chmod 777 /home/YOURUSERNAME/Documents/filename.fileextension

Note that the command line is case sensitive. Try that and get back to us.

BTW: Terminal is located at the main menu Applications->Accessories->Terminal

Good luck!
Tried it, no luck; still opens as "Read-only"

I even double-checked the directory; it's correct.

---

