---
title: "Undelete files"
date: 2011-01-15
forum: General Help
---

### Post by ajack38 on 2011-01-15
Hi, I accidentally permanently deleted a few files and I was wondering if there was a program that finds the files that were deleted and restores them?

---

### Post by tobold on 2011-01-15
Hi,

you may try to find the deleted files by opening a terminal and typing: 

sudo nautilus

After providing the super user password, a new file browser windows should open.

Now click on "File System" and open "home".

Press CTRL+ H.

A hidden folder named .Trash-0 should appear. Navigate to .Trash-0/files , maybe you'll find your deleted files here.

Cheers

---

### Post by ajack38 on 2011-01-15
Thanks for the quick reply. But that didn't work, I went to filesystem then home and Pressed CTRL + H and It just stayed the same by showing the folders of the usernames.

---

### Post by Rhubarb on 2011-01-15
Try using **photorec** from the **testdisk** package in the ubuntu repositories.
photorec is able to recover many file types (photos, documents, videos, sound).
It needs to be run as root (sudo photorec), and you need another disk for it to dump recovered files on to (such as a big usb drive, another hard drive).
It's a command-line app - there should be some basic tutorials about how to use it online somewhere.

---

### Post by ajack38 on 2011-01-15
Thanks, I'll look into that.

---

