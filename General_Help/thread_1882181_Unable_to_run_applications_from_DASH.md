---
title: "Unable to run applications from DASH"
date: 2011-11-16
forum: General Help
---

### Post by Toyota4Runner on 2011-11-16
This just started to happen today.  If I click on the DASH icon and click on any of the options there (Media Apps, Internet Apps, More Apps) nothing happens.  If I search for an application (ie xterm, gedit, terminal) it will not find anything and just list my documents, downloads and music files.  If I press ALT-F2 and try to run xterm and press enter nothing happens and it remains on the Run screen.

I have attempted in resetting unity and unity icons.  I uninstalled unity-2d and reinstalled.  Rebooted and still the same thing.  Any help will be much appreciated to get this backup and running as I can't run any applications other than the ones on the side dock launcher.

Ubuntu 11.10
Unity-2D
32-bit
All updates applied as of today

---

### Post by Toyota4Runner on 2011-11-17
I created a new user (NewUser) as only 1 user was being used to test it out. I logged in as NewUser, clicking on the DASH I was able to search for and run programs from there. I then renamed the affected users account directory to User_BAD and created a fresh new folder User. I logged back in with the account User and I was once again able to run and search programs from the DASH. I then copied all the personal folders over from the User_BAD folder to User folder. Looks like something went corrupt with the profile directory.

---

