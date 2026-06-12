---
title: "Any alternative to photorec?"
date: 2011-06-23
forum: General Help
---

### Post by arunharidas on 2011-06-23
Hi,

I accidentally deleted my drive, which was an ext4 filesystem. I had lot of .php files in that drive.I created again an ext4 filesystem from that deleted partition. When i used photorec ,it recovered lot of files without the filenames. Can anyone suggest a better recovery tool which recovers both file and the filename?

thanks

---

### Post by inameiname on 2011-06-23
I'm afraid there aren't too many out there. Scalpel is one, which is in the repos. Here is an article about it:

[http://flossstuff.wordpress.com/2011/05/18/recover-your-deleted-files-in-linux-using-scalpel-utility/](http://flossstuff.wordpress.com/2011/05/18/recover-your-deleted-files-in-linux-using-scalpel-utility/)

Extundelete is another.

[http://www.thelinuxgeeks.info/2011/01/04/recover-deleted-files-with-extundelete/](http://www.thelinuxgeeks.info/2011/01/04/recover-deleted-files-with-extundelete/)

Foremost is the best, but its a bit outdated, and I don't think it supports Ext4 (not sure, though).:

[http://www.brighthub.com/computing/linux/articles/34156.aspx](http://www.brighthub.com/computing/linux/articles/34156.aspx)


Also, maybe this:

[http://www.ehow.com/how_2064953_recover-deleted-files-linux.html](http://www.ehow.com/how_2064953_recover-deleted-files-linux.html)

---

### Post by doas777 on 2011-06-23
if you deleted a whole partition, [testdisk]("https://help.ubuntu.com/community/DataRecovery") is the best tool as it is for recovering the entire partition in addition to any files on it. since it recovers both the file data and the metadata that the filesystem uses for naming and fragment location, it should result in complete recovery assuming your disk is recoverable. just be sure to recover to a differant drive than the one you lost the data off. 

photorec and the tools that inameiname suggested are data carving utilities. for data carving to work, the file needs to have predictable data structures that indicate the beginning and end of the file, so they only work for formatted data types (usually binary) like images that have header and footer "marks" that indicate teh beggining and end of the file. fragmentation can also interfer with this task, as the header and footer data are on differant parts of the disk, but the infomation linking the fragments has been lost with the filesystem tables.

since php files are just text files and text data does not have header/footer marks (they are just raw ascii/unicode data), no data carving utility will be able to reliably recover them. same goes for most source code file types.

---

### Post by inameiname on 2011-06-23
> **doas777 said:**
> if you deleted a whole partition, testdisk is the best tool as it is for recovering the entire partition in addition to any files on it. 

photorec and the tools that inameiname suggested are data carving utilities. for data carving to work, the file needs to have predictable data structures that indicate the beginning and end of the file, so they only work for formatted data types (usually binary) like images that have header and footer "marks" that indicate teh beggining and end of the file. fragmentation can also interfer with this task, as the header and footer data are on differant parts of the disk, but the infomation linking the fragments has been lost with the filesystem tables.


Thanks for a better explanation on those I mentioned. I only know of them, and haven't really used them other than for the fun of it a couple of times.

---

