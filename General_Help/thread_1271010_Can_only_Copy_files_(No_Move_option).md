---
title: "Can only Copy files (No Move option)"
date: 2009-09-20
forum: General Help
---

### Post by acer34e on 2009-09-20
This problem exists on two external, ntfs formatted hard drives I have. They automount with ntfs-3g and I am able to read/write to them perfectly. The problem/question I am encountering is that I cannot move files between directories on the drive by dragging them from their current location to the destination folder. They automatically begin to copy.
An example is highlighting file1.txt and file2.avi in directory /media/disk and dragging them to /media/disk/folder1. This should be a simple move, but it begins a copy process. I am able to move the files with the mv command in a terminal without sudo privileges. Am I missing something here?
Thank you for your support.

---

### Post by acer34e on 2009-09-20
This is a bump, but with more information:
When I plug in a Fat32 formatted USB device I am able to move files within a device by dragging and dropping. Is this a known ntfs issue? Is it a thunar problem? Keep in mind I can move files from the command line, but would like to be able to do it graphically as well.
Anybody else have an idea?

---

### Post by erilidon on 2009-09-20
try cut and paste?

I have never tried to move a file between two ntfs drives as I do not use it, But I also do not see why it shouldn't work.

---

### Post by sideaway on 2009-09-20
I believe the copy process you are experiencing is deliberate... drag and drop for external drives (atleast with mine) has always been a copy function.

---

