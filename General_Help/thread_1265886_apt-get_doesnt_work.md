---
title: "apt-get doesnt work"
date: 2009-09-14
forum: General Help
---

### Post by thecow on 2009-09-14
Hello, I recently uninstalled open-office by the following command:
sudo apt-get remove openoffice*

It then tried to remove everything but didn't finish and crashed.  Now whenever I try to run apt-get it tells me to run apt-get -f install

So Ive tried that and eventually it asks me if I want to proceed.  So I type in yes and it says this:

```

The following extra packages will be installed:
  openoffice.org-base openoffice.org-base-core openoffice.org-common
  openoffice.org-core openoffice.org-java-common openoffice.org-style-human
Suggested packages:
  libmyodbc odbc-postgresql libsqliteodbc tdsodbc mdbtools libmysql-java
  libpg-java libjtds-java openoffice.org-gcj openoffice.org-report-builder
  openoffice.org-style-industrial openoffice.org-style-hicontrast
  openoffice.org-style-tango openoffice.org-style-crystal
  openoffice.org-style-oxygen xfonts-mathml
The following packages will be REMOVED:
  openoffice.org-hyphenation-en-us
The following NEW packages will be installed:
  openoffice.org-base openoffice.org-base-core openoffice.org-common
  openoffice.org-core openoffice.org-java-common openoffice.org-style-human
0 upgraded, 6 newly installed, 1 to remove and 2 not upgraded.
2 not fully installed or removed.
Need to get 0B/57.0MB of archives.
After this operation, 195MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 317362 files and directories currently installed.)
Removing openoffice.org-hyphenation-en-us ...
/var/lib/dpkg/info/openoffice.org-hyphenation-en-us.postrm: 6: update-openoffice-dicts: not found
dpkg: error processing openoffice.org-hyphenation-en-us (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 openoffice.org-hyphenation-en-us
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


I also can't access the Add/Remove software part of the Applications screen.  I am using Ubuntu 9.04.  Something horrible happened when I tried to remove openoffice that is for sure.

Thank you for your time

---

### Post by jualin on 2009-09-14
Try > sudo apt-get update and then try again using the apt-get install command. Hope this helps!

---

### Post by thecow on 2009-09-14
Still gives me the same error

---

### Post by falconindy on 2009-09-14
Try resolving the dependencies in synaptic. There's a filter on the left hand side that will easily show you any and all broken packages.

---

### Post by thecow on 2009-09-14
Ah I tried that and nothing.  It doesn't show any broken packages.  I am getting the same error:

Errors were encountered while processing:
 openoffice.org-hyphenation-en-us


This keeps hanging it up

---

### Post by DiegoTc on 2009-09-14
I will sound strange, but why you don't try 
sudo aptitude install

It may help I got a similar problem like that once.

---

### Post by thecow on 2009-09-14
That actually did fix some other problems I was having by removing packages I didn't need.  i couldn't get to them because apt-get was failing.  However it didnt fix the main issue.

I did get it fixed however and I just basically did the following from:

[http://ubuntuforums.org/showthread.php?t=698140](http://ubuntuforums.org/showthread.php?t=698140)


sudo mv /var/lib/dpkg/info/openoffice.org-hyphenation.postrm /var/lib/dpkg/info/openoffice.org-hyphenation.postrm.bak

That command fixed it, and I have no idea why.  Very strange, anyways it works now.


Edit: Actually that didn't work fully as it would still complain about that file.  I just literally went into that file with emacs and deleted a line it was complaining about.  "update-openoffice-dicts"  Then apt-get completed fine.  Phew.  Though we'll see if that affects the functionality of OpenOffice.org in some way. This might not be over I guess

---

