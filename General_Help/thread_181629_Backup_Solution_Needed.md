---
title: "Backup Solution Needed"
date: 2006-05-24
forum: General Help
---

### Post by toran on 2006-05-24
Hello all.

I would like to back up to DVD some very large directories. I am constantly adding new contents to these directories. My need is this: I would like a program that could keep track of what I already have written and detect what more needs to be backed up to more DVDs. 

Does anyone know of a program that can do this?

Thanks.

---

### Post by aysiu on 2006-05-24
KDar?

---

### Post by bbrand on 2006-05-24
Good old "tar" works for me with the bzip2 option turned on. You end up with a compressed backup that you can write to a server or burn to a dvd. I have created a shell script that does the backup and then burns the dvd. I pop in a blank dvd before going to bed and then have a backed up system in the morn.

---

### Post by simonn on 2006-05-24
How many dvds are you looking at?

I have a similar issue. I bought a Squeezebox 3 ([http://www.slimdevices.com](http://www.slimdevices.com)) and have around 100Gb of music to keep backed up. As it took me literally weeks to rip my CDs (no CD ripping service in Oz), I do not consider using the original CD as the equivalent of a backup as viable (other than as a last resort if I lose both hard drives at the same time, see below).

IMHO, if you have more than a handful of DVDs worth of data to backup, use an external hard drive, which you only plug in when you do a backup, and rsync. Do not use an internal harddrive because if the PC is taken out by a power surge, faulty PSU or drive controller or something you risk losing the backup at the same time.

The risk of both drives failing at the same time is small, so I am happy to live with just that, but you may want to consider something else on top of this as well, e.g. backing up a snapshot to DVD or another harddrive periodically and storing off-site as well. 

This is all depending on how valuable you consider your data.

In answer to your original question...

It would be trivial to roll your own utility to do this.

You could do a find on the directory tree(s) and direct the output to a file before or immediately after you do a backup. This will give you a list of the files you are about to or have just backed up.

The next time you do a backup do another find and direct it to a file.

Then do a diff between the files. This will give you a list of the new files to backup.

---

