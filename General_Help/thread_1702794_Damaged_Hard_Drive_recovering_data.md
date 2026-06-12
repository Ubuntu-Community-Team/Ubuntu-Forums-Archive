---
title: "Damaged Hard Drive recovering data?"
date: 2011-03-08
forum: General Help
---

### Post by the lemming on 2011-03-08
Hello

One of my 1TB (NTFS) hard drives has developed a fault and I can not read any data on it.

Its connected to a Windows7 OS and I get the error message which says that the file structure is damaged.

Is there any way that I can restore the file system or recover my personal data of movies, photos and music.

I do have a backup on an external drive but the backup is 3 months old and I'm hoping to recover this years photos as a priority.

Cheers

---

### Post by oldfred on 2011-03-08
With NTFS you want to run chkdsk to see if it can repair itself.

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)


If that does not work you can try testdisk:
If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

After that then you can use photrec which just scans drive for any data that looks like a file. It can take hours/days with large drives and does not recover names. But photos & music have internal metadata that can be used to recover a name.  You have to have another drive with the same amount of space of the data you may recover. It also recovers deleted data so you have to have a large drive available.

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by the lemming on 2011-03-08
Thanks for the links and advice.

Cheers

---

