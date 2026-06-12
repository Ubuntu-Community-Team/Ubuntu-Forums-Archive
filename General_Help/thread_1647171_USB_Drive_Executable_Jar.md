---
title: "USB Drive Executable Jar"
date: 2010-12-16
forum: General Help
---

### Post by Cosmic1 on 2010-12-16
I'm trying to mark a jar file as executable inside a flash drive (/media/flashDriveName). When I go into the file properties and mark the checkbox "allow executable", then it immediately unmarks it. Also I tried to run "sudo chmod +x /media/flashDriveName" but that didn't actually do anything. Any idea what's wrong or how I can get around that?

---

### Post by efflandt on 2010-12-16
What type of file system is on the flash drive?  Some file systems (like FAT32 typical for flash drives) have no concept of ownership or file permissions.  So either all files will appear to have execute permission, or none will, depending upon mount options.

---

### Post by Cosmic1 on 2010-12-16
In the device's properties it says:

Filesystem type: msdos

you think that's the problem? If it is is there any way to get around it without moving the file off of the flash drive? I am writing a java application for semi-personal use so I want it to be as portable as possible on a flash drive.

---

