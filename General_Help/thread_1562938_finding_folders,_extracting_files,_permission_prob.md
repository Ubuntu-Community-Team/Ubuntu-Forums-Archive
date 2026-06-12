---
title: "finding folders, extracting files, permission problems"
date: 2010-08-28
forum: General Help
---

### Post by scur on 2010-08-28
new to ubuntu and linux, and using Lucid 10.04 LTS

ok, i'm trying to get XBMC going, and following a nice step by step instruction on wiki.xbmc.org, but now i'm stuck at this step...

In Ubuntu the SVN Repositories are not automatically added. You must add them manually.
First, download the SVN Repo Installer from:
[http://xbmc-addons.googlecode.com/svn/packages/plugins/programs/SVN_Repo_Installer.zip](http://xbmc-addons.googlecode.com/svn/packages/plugins/programs/SVN_Repo_Installer.zip)
Extract it to the ~/.xbmc/plugins/programs directory. If this directory does not exist, run XBMC one time and then exit back to Ubuntu. The directory should now exist.


i ran xbmc once (after the video driver problem was solved, though it messed up my dual monitors, gotta figure that one out yet.) i got the zip file, it's in my downloads. now my newbness really shows...
i can't find an 'extract' command for gnome, can't find the .xbmc directory using the file browser, can't figure out how to hunt for folders instead of files, and don't know how to look inside folders i don't have permission to, that is, i don't know if there's a 'sudo' like option for the file browser.
i've been searching the forums, but without the correct search terms, i'm wading in an ocean. i really want to give ubuntu an honest try, but i feel like a foreigner.

EDIT: btw, up to this point, the forums have been invaluable, you all are great.

---

### Post by geirha on 2010-08-28
For zip files, make sure the [unzip](apt:unzip) package is installed, then you can double click a zip file and extract it (or right click a zip file and choose extract here).

Files starting with a dot are considered "hidden" by nautilus (the file browser). You can hit Ctrl+h to toggle showing hidden files.

There is an extension to nautilus that allows you to right-click and choose Open as administrator. The package to install is [nautilus-gksu](apt:nautilus-gksu). After installing it you need to log out and back in again (or otherwise restart nautilus).

---

### Post by scur on 2010-08-29
good nuggets, thnx much!

---

