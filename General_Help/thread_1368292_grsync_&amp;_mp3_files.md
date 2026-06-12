---
title: "grsync &amp; mp3 files"
date: 2009-12-30
forum: General Help
---

### Post by IGITIHI on 2009-12-30
I am using grsync to backup my mp3 folders to a usb hard disk drive (filesystem type: msdos). My collection is pretty big (more than 150 GB) and sometimes I update the tags of the mp3 files and I would like the backup file tags to be updated as well. 

I activated the following options: preserve time, delete on destination, verbose, ignore existing. 

The problem is that with "ignore existing" enabled, rsync does not update files whose tags have been changed. If I deactivate "ignore existing", the backup takes ages because it copies every file. Is there an option that will allow rsync to detect that a tag has been changed and update the corresponding file? Always checksum maybe?

---

### Post by b0b138 on 2009-12-30
Try skip newer instead.  If you have ignore existing selected, it won't update files that already exist on your usb drive. After you remove ignore existing, run it and let it back up everything. Then edit a file and run it again (or choose a smaller folder for testing rather than your whole mp3 folder)

---

