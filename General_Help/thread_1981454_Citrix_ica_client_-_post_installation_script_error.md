---
title: "Citrix ica client - post installation script error"
date: 2012-05-16
forum: General Help
---

### Post by marscoast on 2012-05-16
I recently upgraded my workstation to 12.04-desktop-amd64 and set up a new one for my father-in-law.  On mine I had to upgrade the citrix client, while on the other I did a fresh install.  I used the latest deb package available on their site: icaclient_12.1.0_amd64.deb.

The good news; it installs and works just fine.  However at the end of the install, I get an error about a "post installation script" giving a return value of 2.  Like I said, the ica client works just fine, so I'm not too worried about the error.  But here is the problem - whenever I install a package now (through the USC gui, apt-get, or dpkg) the installer "revisits" that error and pops it up again.  This is happening on both hosts.  So how do I get the installer (dpkg, right?) to just "get over it" and forget about that error?

---

### Post by Toz on 2012-05-16
Hello and welcome to the forums.

I believe the issue has been resolved [here]("http://forums.citrix.com/thread.jspa?threadID=306353&tstart=0").

---

