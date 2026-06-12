---
title: "google-dosc-fs installation probem"
date: 2010-05-09
forum: General Help
---

### Post by barnskybeat on 2010-05-09
I am attempting to install google-docs-fs (fuse module for google docs) but receive the following error message:

google-docs-fs:
Depends: python-gdata (>=1.3.0) but 1.2.4-0ubuntu2 is to be installed

I tried uninstalling phython-gdata and downloaded a newer version (2.0.9) but are unable to install it.

I am not too good in terminal and need some help to get google-docs-fs installed and running.
Thanks
barnskybeat

---

### Post by WorMzy on 2010-05-09
I assume you downloaded it from here: [http://code.google.com/p/gdata-python-client/](http://code.google.com/p/gdata-python-client/)

Did you check out the readme.txt you get in the gdata archive?

I'll assume you downloaded to your /home/user/Downloads folder. First, open a terminal and change directories with ```
cd ~/Downloads
``` Next extract the contents of the archive with ```
gzip -dc gdata-2.0.9.tar.gz | tar xf -
``` Next move into the folder you just extracted with ```
cd gdata-2.0.9
``` Finally, run```
sudo python setup.py install
```
And you're done. You now have gdata2.0.9 installed. Unless you got an error. In which case, post it here and hopefully we can figure out what went wrong.

---

### Post by barnskybeat on 2010-05-09
many thanks, the gdata installation in terminal went fine, no error messages.
However, still can't install google-doc-fs and now receive the following error message: 

google-docs-fs:
 Depends: python-gdata but it is not going to be installed

Please note that python-gdata (1.2.4 OUbuntu2) is not installed any more.
how can I verify that the gdata 2 is properly installed and fix the above error?
barnskybeat

---

### Post by WorMzy on 2010-05-09
I guess installing using the python script didn't work because it didn't update the package manager. There's probably a way around that, but I have no idea how you'd go about it.

But don't worry, I have a solution. Download and install this file: [http://google-docs-fs.googlecode.com/files/python-gdata_2.0.7-1_all.deb](http://google-docs-fs.googlecode.com/files/python-gdata_2.0.7-1_all.deb)

It _does_ update the package manager, so then the dependency should be met and you'll (hopefully) be able to install google-docs-fs.

---

### Post by barnskybeat on 2010-05-09
I downloaded the .deb package and attempted to install.This is the error I get:
Error: Dependency is not satisfiable: python-gdata (>= 1.3.0)

---

### Post by WorMzy on 2010-05-09
You get that from the gdata deb file, or the google-docs-fs deb file?

You really shouldn't be getting it for the gdata deb, because it shouldn't be depending on an earlier version of itself. And the google-docs-fs deb file shouldn't be complaining if you've installed the the dgata deb, because that deb installs dgata 2.0.7.

I'm testing this on my machine, and the google-docs-fs deb file is saying all dependencies are met..

Try installing this package: [http://google-docs-fs.googlecode.com/files/python-gdata_2.0.7-1_i386.deb](http://google-docs-fs.googlecode.com/files/python-gdata_2.0.7-1_i386.deb)

---

### Post by barnskybeat on 2010-05-09
I am getting the error from the google-docs-fs deb file you advsied me to download.

---

### Post by WorMzy on 2010-05-09
I didn't advise you to download google-docs-fs, that first link was to a deb for installing gdata, the second link is a different deb file for installing gdata.

---

### Post by barnskybeat on 2010-05-09
I followed this link:
"But don't worry, I have a solution. Download and install this file: http://google-docs-fs.googlecode.com....0.7-1_all.deb" 
downloaded the file to downloads folder and selected open with package installer.this installer does gives me the error message.

---

### Post by barnskybeat on 2010-05-09
I think I now followed the correct link:
"Try installing this package: http://google-docs-fs.googlecode.com...0.7-1_i386.deb" installed the package and also google-docs-fs afterwards without problems.
Thanks a lot for your expert help and patience,much appreciated!
barnskybeat

---

### Post by WorMzy on 2010-05-09
That is very strange.

Have you tried the second link?

Edit: No problem. I'm glad I could help. :)

---

