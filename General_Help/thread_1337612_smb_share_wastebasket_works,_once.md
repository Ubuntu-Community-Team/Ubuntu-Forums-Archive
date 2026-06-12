---
title: "smb share wastebasket works, once"
date: 2009-11-25
forum: General Help
---

### Post by bobtpenguin on 2009-11-25
Hello all,
I've just installed 9.10.  I've got an smb share mounted off my NAS system by the following line in fstab:
```

//192.168.1.5/shared /mnt/smbshare cifs uid=1000,rw,username="guest",password="" 0 0
```the share mounts and I can read and right files to it.  The **very first time** I delete a file from the share the file is moved to a new folder called /mnt/smbshare/.Trash-1000 and the file shows up in the nautilus wastebasket.  If I restart the machine and then access the wastebasket the deleted file does not show up, but it is in /mnt/smbshare/.Trash-1000/files.  If I delete /mnt/smbshare/.Trash-1000 then delete another file from /mnt/smbshare that file is moved to a newly created /mnt/smbshare/.Trash-1000 and it shows up in nautilus wastebasket!

What's going on?  It's almost as though gvfs isn't scanning mount points for .Trash-XXXX folders and linking them to nautilus wastebasket.

Many thanks
BobTPenguin

---

