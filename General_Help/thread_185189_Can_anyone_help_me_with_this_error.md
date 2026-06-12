---
title: "Can anyone help me with this error?"
date: 2006-05-31
forum: General Help
---

### Post by novik420 on 2006-05-31
This is what happens when i try to install wine with synaptic nad go to mark for installation 





Could not mark all packages for installation or upgrade.

The following packages have unresolved dependencies. Make sure that all required repositories are added and enabled in the preferences.

wine:
  Depends: libartsc0 (>=1.5.2-0) but 1.5.1-0ubuntu0breezy1 is to be installed
  Depends: libasound2 (>1.0.10) but 1.0.9-2 is to be installed
  Depends: libgcc1 (>=1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
  Depends: libglib2.0-0 (>=2.10.0) but 2.8.3-0ubuntu1 is to be installed
  Depends: libstdc++6 (>=4.0.2-4) but 4.0.1-4ubuntu9 is to be installed
  Depends: libxml2 (>=2.6.24) but 2.6.21-0ubuntu1 is to be installed

---

### Post by frodon on 2006-05-31
I think you don't have all the repositories enabled, you will find in the link below how to add them : 
[http://ubuntuforums.org/showthread.php?t=153118](http://ubuntuforums.org/showthread.php?t=153118)

---

### Post by Sef on 2006-05-31
To add the repositories, [click here.]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

---

### Post by novik420 on 2006-05-31
I have tried those and i seem to be still getting the same error

---

### Post by honeydew on 2006-05-31
maybe try the wine directions

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by YokoZar on 2006-06-01
You're not by any chance trying to install the dapper packages onto breezy are you?  They depend on the dapper versions of the libraries they were built with.

After ensuring you're using the right repositories, try running apt-get dist-upgrade to get your packages up to date.

---

### Post by honeydew on 2006-06-01
I used the link I suggested earlier to install wine on dapper.. and it installed with out any problems..

---

