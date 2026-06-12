---
title: "Help using Scalpel to recover files deleted from Trash"
date: 2011-06-07
forum: General Help
---

### Post by tuathan on 2011-06-07
I used Scalpel to try and recover .doc files from a directory I accidentally placed in the Trash can and then emptied:

```
$ sudo scalpel /dev/sda5 -o output
Scalpel version 1.60
Written by Golden G. Richard III, based on Foremost 0.69.

Opening target "/dev/sda5"
/dev/sda5: 100.0% |******************************************************************************************************************|   67.0 GB    00:00 ETAAllocating work queues...
Work queues allocation complete. Building carve lists...
Carve lists built.  Workload:
doc with header "\xd0\xcf\x11\xe0\xa1\xb1\x1a\xe1\x00\x00" and footer "\xd0\xcf\x11\xe0\xa1\xb1\x1a\xe1\x00\x00" --> 460 files
doc with header "\xd0\xcf\x11\xe0\xa1\xb1" and footer "" --> 486 files
/dev/sda5: 100.0% |******************************************************************************************************************|   67.0 GB    00:00 ETAProcessing of image file complete. Cleaning up...
Done.
Scalpel is done, files carved = 946, elapsed = 2910 seconds.

```

The program appears to execute ok. It creates a directory called /home/output but this seems to be empty (4.0 K) and when i try to cd into the directory i get the following:

```
cd output/
bash: cd: output/: Permission denied

```

Has Scalpel recovered any files and where are they located?

Many thanks for your help.

---

### Post by UltraAnders on 2011-06-08
I had the same problem using  foremost to recover some files from an SD card.

You cannot access the directory from the command prompt because it's created with the owner "root". You can use "chown" to change the owner of the directory and all files within using this command.```
sudo chown -R -v -P username:username ./output/
```You'll need to be in the directory containing the folder "output". Change "username" to whatever your username is.

---

### Post by tuathan on 2011-06-09
yeah thanks. figured that out right after i posted the thread here :smile:

---

