---
title: "ubuntu 10.04 crash caused by firefox 3.6"
date: 2011-04-05
forum: General Help
---

### Post by adrian_nye on 2011-04-05
I have ubuntu 10.04.2 and firefox 3.6.2 running on an Acer 5732 laptop.  All updates are applied.

This combination has run fine until today.  I opened a weather site (long term forecast on weather underground I think) and the system completely froze, nothing on the screen would do anything, mouse and keyboard both dead, so I ended up pushing the power button to reboot.

Now if I try to use firefox the same thing happens every time.   How do I reset firefox to make it stop trying to open this
web page?

---

### Post by lithopsian on 2011-04-05
Profile might be corrupt.  Or it may keep trying to restore to that same bad (cached?) page.  Start in safe mode by using command line parameter --safe-mode.  If that works then you can see what bits of your profile you can safely keep.

Also, upgrade to a more recent version of Firefox.  You're a long way out of date there.

---

### Post by adrian_nye on 2011-04-05
i removed  ~/.mozilla/firefox/m????/sessionstore.js and
firefox runs again.

---

