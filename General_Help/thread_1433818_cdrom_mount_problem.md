---
title: "cdrom mount problem"
date: 2010-03-19
forum: General Help
---

### Post by DaveCason on 2010-03-19
Hi,
 
I just setup a new server 8.04
How can I move a file from a cd-rom in the temp folder?
 
 
I don't know if it's auto mounting and I can't find the right way to mount it.
 
Here's the fstab:
 
/dev/sda1         ext3
/dev/sda5         swap
/dev/scd0         /media/cdrom0      udf,iso9660,user,noauto, exec,uft8   0   0  
 
 
Cheers'
Dave

---

### Post by DaveCason on 2010-03-19
OK, so I try:
 
sudo mount /dev/scd0 /dev/cdrom0
 
and all I get is a scrolling error string that says:
 
- Buffer I/O erro on device sr0, logical block XXXXXX
 
 
Cheers'
Dave

---

### Post by jobix on 2010-03-19
"mount -l" will show you a list of the mounted filesystems. The "noauto" in your fstab would seem to indicate that it is not being auto-mounted. Just for the heck of it, does "ls -l /media/cdrom0" show anything? Also, are you sure the CD that you're trying to read from is not corrupt? Can you read it from somewhere else (a different machine)?

---

