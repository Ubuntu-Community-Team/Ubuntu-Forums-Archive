---
title: "Dropbox Installation Issue - Hang, quit without startup after installation"
date: 2010-05-21
forum: General Help
---

### Post by ok123jump on 2010-05-21
Hello everyone,

This is a solution post, not a problem.

I will walk you through how to fix the hang and quit issue with Dropbox 0.62 if you've had problems like mine.

_The Problem Setup:_
I used to run Ubuntu 9.10, but then decided to upgrade to 10.04. Upon doing so, my old Likewise Network login didn't work anymore. After sacrificing some sleep and many hours, I managed to reconfigure the new Likewise, rejoin my Active Directory. This, of course, didn't allow me to use the same Login procedure or info, so I migrated all of my old files to my new login.

_The Issue:_
I ran into the issue that there was a previous installation of Dropbox on the computer (prior to upgrade) which didn't function now. So, I attempted to download Dropbox from [Dropbox Download]("http://www.dropbox.com/downloading") and re-install the package. After walking through the entire installation process, I would get to the screen which says "Start Dropbox" with the icon saying the same. After clicking that, I was notified that I would need to download Dropbox's software and install it. After downloading, it would unpack, hang, then quit without starting dropbox.

_The Solution:_
To solve this problem, open your Home Folder, then press ctrl-h to view hidden folders and delete your .dropbox-dist folder.

I deleted all .dropbox folders, but then subsequently found out that only the first needed to be deleted.

Enjoy. May you have fewer headaches than I had. :popcorn:

---

### Post by celem on 2010-05-24
Worked for me - thanks!

---

### Post by neoxl on 2010-09-09
Worked for my beta MM installation as well! Thanks a lot! :p

---

