---
title: "Backup Script using tar"
date: 2010-01-24
forum: General Help
---

### Post by Lutherian on 2010-01-24
Hi, here's an easy one for the real hackers out there

I'd like to make a script that backs up each folder (named specifically in the script) into a single (uncompressed) tar file.

something along the lines of

# Backup Script
tar -??? /media/disk-1/folder1/ /media/disk-2/folder-1.tar
tar -?? /media/disk-2/folder2/ /media/disk-2/folder-2.tar

where -?? are the correct options (command line switches). I've looked at the man pages, but some of the options seem ambiguous to me, so many options - amazing!

this is just something to backup my portable usb drive (ext3 filesystem) to my backup drive (ext3 filesystem) - both USB drives.

== Once the .tar file have been created ==

reading the man pages, I saw the option of incremental backups.
Would it be possible to create a backup script that will only update new files and remove deleted (source) files from tar (target) files?
i.e which are the best combination of command line switches, once again there seem to be several option - I'm not sure of the right path.

I know the info is available in the man pages, but this is more a case of caution than laziness.

Thanks to all

---

### Post by Lutherian on 2010-01-24
tar -vcf /media/disk1/folder1.tar /media/disk2/folder1/

---

### Post by Lutherian on 2010-01-24
Ammendment:
I will add the (i)gnore errors option, as I am getting "input-output" errors during copying. It's probably a sign that my drive has some corruptions on it. This I need to get the data backed up as soon as possible.

tar -vicf /media/disk1/folder1.tar /media/disk2/folder1/

---

