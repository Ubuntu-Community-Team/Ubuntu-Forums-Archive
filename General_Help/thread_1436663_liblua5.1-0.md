---
title: "liblua5.1-0"
date: 2010-03-22
forum: General Help
---

### Post by JohnJD on 2010-03-22
I am getting this error whenever I try to download something from the software-center:

```

installArchives() failed: Selecting previously deselected package liblua5.1-0. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15%dpkg: unrecoverable fatal error, aborting: 
 files list file for package 'apport-symptoms' is missing final newline 

```

Anyone know what this means?

---

### Post by JohnJD on 2010-03-23
anybody?

---

### Post by JohnJD on 2010-03-24
Okay, I fixed it.  Here is how incase anyone else reads this (although there are probably easier ways):
 
Somehow alot of my packages and files got corrupted when I installed, but for some reason all those same packages installed fine on my laptop.  So, I basically removed /var/lib/dpkg/info--which had a corrupted apport-symptoms.list among many others--and made a copy of the same folder from my laptop, and used it to replace the folder on my desktop.  Did a sudo --configure -a and now everything seems to be working fine.

---

### Post by gmargo on 2010-03-24
I recently posted a perl script that will regenerate the contents of the /var/lib/dpkg/info/ directory, using package lists and the status file and lots of downloading .deb files.  You can run it in summary mode (the default) to see if anything seems to be missing.  See this post: [http://ubuntuforums.org/showpost.php?p=8991214&postcount=19](http://ubuntuforums.org/showpost.php?p=8991214&postcount=19)

---

