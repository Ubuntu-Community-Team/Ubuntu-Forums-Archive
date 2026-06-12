---
title: "Recovering Data from Overwritten Ext2 Partition"
date: 2012-06-29
forum: General Help
---

### Post by dodle on 2012-06-29
I am trying to recover some files from a hard drive that was primarily an Ext2 partition (there was a small ntfs partition at the beginning). The current filesystem is fat32 but formatting did not finish so it is unreadable at the moment. I am currently running photorec on it but it hasn't found anything yet. Does anyone have any suggestions on how I might be able to recover the files. Should I reformat it back to Ext2 before trying to recover? This is the first time I have attempted file recovery on a filesystem type other than ntfs and fat.

**----- Edit -----**

Okay, photorec just started recovering files. I was able to do it without reformatting the drive. Hopefully it doesn't just search for files based on extension.

---

### Post by oldfred on 2012-06-30
Photorec is a low level recovery, it does only find based on extension or type of file it sees as it scans hard drive.

Some tools to help:
Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

If not reformated but a partition error change on type, you can sometimes restore type with Disk Utility (not reformat, but just change type). Or testdisk sometimes can restore. If testdisk works it does restore full file name. Always best to do an image backup first so you have a way to restore if attempting to repair fails.

---

