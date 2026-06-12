---
title: "cant install a deb package in Lubuntu (Opera Web Browser)"
date: 2011-07-01
forum: General Help
---

### Post by samMD on 2011-07-01
everytime I try to install the .deb package from the opera browser web site in Lubuntu, I get the text based installer (looks like command prompt). I follow the instructions "press I" to install, and even include sudo before the "I" all it says install "Done" press <return> to continue, and the installer quit not installing anything.

I even get this message: eval: 1: default: not found

---

### Post by collisionystm on 2011-07-01
> **samMD said:**
> everytime I try to install the .deb package from the opera browser web site in Lubuntu, I get the text based installer (looks like command prompt). I follow the instructions "press I" to install, and even include sudo before the "I" all it says install "Done" press <return> to continue, and the installer quit not installing anything.

I even get this message: eval: 1: default: not found

Open Terminal

Browse to your Folder containing the opera .deb

Assumingly Downloads

cd /home/user/Downloads

sudo dpkg -i operafile.deb


What is the output?

---

### Post by samMD on 2011-07-01
the command worked and opera installed here is the output:

> Selecting previously deselected package opera. (Reading database ... 83790 files and directories currently installed.) Unpacking opera (from opera_11.50.1074_i386.deb) ... Setting up opera (11.50.1074) ... update-alternatives: using /usr/bin/opera to provide /usr/bin/x-www-browser (x-www-browser) in auto mode. Error in file "/usr/share/applications/gnumeric.desktop": "zz-application/zz-winassoc-xls" is an invalid MIME type ("zz-application" is an unregistered media type) Processing triggers for shared-mime-info ... Processing triggers for desktop-file-utils ... Processing triggers for hicolor-icon-theme ... Processing triggers for man-db ... sam@samnetbook:~/Downloads$ ^C sam@samnetbook:~/Downloads$

---

### Post by collisionystm on 2011-07-01
Great! Glad to here it worked.

---

