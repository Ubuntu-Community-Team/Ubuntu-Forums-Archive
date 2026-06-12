---
title: "Google chrome not starting"
date: 2012-07-01
forum: General Help
---

### Post by Coolmariorocks on 2012-07-01
I am running ubuntu 10.10 (Since this old computer can't handle the newer ubuntu) and Google chrome the latest isn't starting... how do i get it to start working again? Also does anybody know the link to like a older version of google chrome from like 2 versions ago? Please help

---

### Post by cottfcfan on 2012-07-01
There was a problem with Chrome 20, but an upgrade 2 days ago seems to have resolved it, otherwise no problems here.
You could try clearing out your Chrome profile and starting again.
The files are:
Home/.config/google-chrome
Home/.cache/google-chrome

Alternatively you could uninstall Chrome & use Chromium from the repos instead.

---

### Post by Coolmariorocks on 2012-07-01
> **cottfcfan said:**
> There was a problem with Chrome 20, but an upgrade 2 days ago seems to have resolved it, otherwise no problems here.
You could try clearing out your Chrome profile and starting again.
The files are:
Home/.config/google-chrome
Home/.cache/google-chrome

Alternatively you could uninstall Chrome & use Chromium from the repos instead.
I would do that but the flash player plugin from the software center provided by ubuntu isn't working in firefox.. I found chrome 17.. I'm deleting the profile folders and umm going to use chrome 17. hopefully that will work..

---

### Post by cottfcfan on 2012-07-01
Just Googling around and your problem seems to affect other users too.
Could have something to do with the new pepperflash.
[https://code.google.com/p/chromium/issues/detail?id=134940](https://code.google.com/p/chromium/issues/detail?id=134940)

---

### Post by vasa1 on 2012-07-01
> **Coolmariorocks said:**
> I am running ubuntu 10.10 (Since this old computer can't handle the newer ubuntu) and Google chrome the latest isn't starting... how do i get it to start working again? Also does anybody know the link to like a older version of google chrome from like 2 versions ago? Please help

There is [an existing problem]("http://ubuntuforums.org/showthread.php?t=2013233") with Chrome 20 on certain computers. The workaround is to disable the Pepper Flash plug-in and use the other one (which should be seen by Chrome automatically if the user has Firefox that plays Flash successfully).

---

### Post by Coolmariorocks on 2012-07-01
Deleted profile folder and installed chrome 17 from a backup file i had thank goodness i make backups of files.. anyways google-chrome-stable now works with google chrome 17..

---

