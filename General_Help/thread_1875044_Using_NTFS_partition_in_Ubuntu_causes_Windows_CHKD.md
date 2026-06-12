---
title: "Using NTFS partition in Ubuntu causes Windows CHKDSK to fail"
date: 2011-11-04
forum: General Help
---

### Post by sunk_u on 2011-11-04
Hi,

I'm using an NTFS partition on an external hard disk and Back In Time to back up my Ubuntu files. I also run Windows and I would like to read the data in the hard disk from Windows, hence NTFS. I would also like my Windows backup to be on the same drive.

I have a few files in Ubuntu whose names do not pass Windows' naming restrictions, like 'Why so few?.pdf'. When I run CHKDSK on this partition in Windows, I get errors like the following

```

Minor file name errors were detected in file 68777

All filenames for File 68778 are invalid.

Index entry Why so few?.pdf in Index $I30 of file 68071 is incorrect

```

And the Windows Backup utility refuses to use the disk for backup. Is there any way out of this? Perhaps forcing the file names on the back up disk to follow Windows restrictions and yet work with a backup utility?

---

### Post by prodigy_ on 2011-11-04
Windows doesn't recognize characters like **?** as valid in filenames even though NTFS itself does NOT prohibit you from creating filenames with such characters in them.

You should either use only the characters allowed by Windows when you deal with NTFS or manually mount NTFS partitions with **windows_names** option (in this case the driver will check the compatibility for you).

P.S. However, I'm under impression that **chkdsk** doesn't really fail on such errors. Did you run it with /F option?

---

### Post by Mark Phelps on 2011-11-04
If you're doing backups to an external drive, why not just shrink the NTFS partition and add an Ext4 partition solely for backups.  I have that setup and it works great for doing backups and restores using Clonezilla.

---

### Post by sunk_u on 2011-11-04
> **prodigy_ said:**
> 
You should either use only the characters allowed by Windows when you deal with NTFS or manually mount NTFS partitions with **windows_names** option (in this case the driver will check the compatibility for you).


Yes I thought of that, but does the backup utility that work when it is mounted in such a way?

> **prodigy_ said:**
> 

P.S. However, I'm under impression that **chkdsk** doesn't really fail on such errors. Did you run it with /F option?

Well I didn't use the /F option, because if Windows starts changing the filenames, the backup utility on Ubuntu won't recognise the files anymore?


> **Mark Phelps said:**
> If you're doing backups to an external drive, why not just shrink the NTFS partition and add an Ext4 partition solely for backups.

Yes I could, but putting all of them in one partition just gives me more flexibility in managing space. If there's no other option, I'll just do that..

---

### Post by prodigy_ on 2011-11-04
Mark's suggestion is probably the best.

There are other things Windows won't like besides special characters. For example, file names starting with a dot (though chkdsk won't give you any error message about those). For Linux backups you should use a native Linux partition or a backup utility that creates archives (like **tar**).

---

### Post by sunk_u on 2011-11-04
> **prodigy_ said:**
> Mark's suggestion is probably the best.


OK, then I'll just do that.

> **prodigy_ said:**
> 
For Linux backups you should use a native Linux partition or a backup utility that creates archives (like **tar**).

Is there any inherent advantage of using tar over utilities like Back In Time, which uses rsync? The files are more accessible and the backup is incremental, so it takes much less time..

---

### Post by prodigy_ on 2011-11-04
Tar can do incremental backups:
[http://www.gnu.org/software/automake/manual/tar/Incremental-Dumps.html](http://www.gnu.org/software/automake/manual/tar/Incremental-Dumps.html)

The main advantage of this approach in your case is that you won't need a separate partition. But of course files are less accessible when they are archived. :)

---

### Post by sunk_u on 2011-11-04
> **prodigy_ said:**
> Tar can do incremental backups:
[http://www.gnu.org/software/automake/manual/tar/Incremental-Dumps.html](http://www.gnu.org/software/automake/manual/tar/Incremental-Dumps.html)

The main advantage of this approach in your case is that you won't need a separate partition. But of course files are less accessible when they are archived. :)

Great, thank you.

---

