---
title: "/var/backup is too big for dvd copy"
date: 2011-05-31
forum: General Help
---

### Post by spacefrog on 2011-05-31
I made a backup copy of my system before encountering a problem. Now I want to install Ubuntu 11.04 and use the system backup, but I can't copy it to disc because it is just over 10 Gb. Any suggestions? Thanks.

---

### Post by noah++ on 2011-05-31
If your backup comprises a single monolithic image file, [split the file]("http://blulin.wordpress.com/2009/02/07/split-and-join-large-files-in-gnulinux-just-using-terminal/") into small enough parts to burn to two discs. If it's just a file-for-file copy, then take an easy-to-manage subset of the files and burn that to one disc, and burn the remaining ones to a second disc.

Alternatively, you could borrow or buy an external hard drive or thumb drive.

By the way, I am fairly sure that if you choose not to reformat your target partition upon install, your backup subdirectory will not be overwritten. But I wouldn't say I'm sure enough of that to not take these precautions.

---

