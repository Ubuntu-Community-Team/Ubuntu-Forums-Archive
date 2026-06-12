---
title: "update problem"
date: 2010-04-09
forum: General Help
---

### Post by kadafi69 on 2010-04-09
When I sudo apt-get upgrade I get this:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  icedtea-6-jre-cacao: Depends: openjdk-6-jre-headless (= 6b16-1.6.1-3ubuntu3) but 6b16-1.6.1-3ubuntu1 is installed
  tzdata-java: Depends: tzdata (= 2010h-0ubuntu0.9.10) but 2010e-0ubuntu0.9.10 is installed
E: Unmet dependencies. Try using -f.


so then i do sudo apt-get -f install and i get this:

> Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 233503 files and directories currently installed.)
Preparing to replace tzdata 2010e-0ubuntu0.9.10 (using .../tzdata_2010h-0ubuntu0.9.10_all.deb) ...
Unpacking replacement tzdata ...
dpkg: error processing /var/cache/apt/archives/tzdata_2010h-0ubuntu0.9.10_all.deb (--unpack):
 unable to create `/usr/share/zoneinfo/right/Africa/Nouakchott.dpkg-new' (while processing `./usr/share/zoneinfo/right/Africa/Nouakchott'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/tzdata_2010h-0ubuntu0.9.10_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

it seems that one the drives is full, any idea how to manually change the disk size by giving it space from another partition. I dont have gparted installed so thats out of the question.

---

### Post by Soul-Sing on 2010-04-09
tzdata seems corrupt. You could try to remove it and reinstall it again.

---

### Post by slooow on 2010-04-09
Is your system on one single partition? Is there more space on the disk? There a lots of solutions to your problem depending how your configuration and backup is. 
A tip which doesn't help you right now, but would avoid such problems in the future is: use the logical volume manager (lvm).
If you have more space on the disk, read this [http://www.gentoo.org/doc/en/articles/partitioning-p1.xml](http://www.gentoo.org/doc/en/articles/partitioning-p1.xml), otherwise you will have to delete something.

---

### Post by kadafi69 on 2010-04-09
no the system is split up into several partitions on the same drive, such as a partition for each / , /usr etc etc, looks like i'll have to delete something before I can do anything.

---

