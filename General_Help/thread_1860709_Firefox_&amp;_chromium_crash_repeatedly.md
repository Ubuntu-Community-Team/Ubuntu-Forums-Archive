---
title: "Firefox &amp; chromium crash repeatedly"
date: 2011-10-15
forum: General Help
---

### Post by deeporbit on 2011-10-15
I did a fresh install of 11.10 this morning. Firefox crashes constantly. I installed Chromium and it's slightly better. I can get about 2 to 3 tabs open and BOOM. I am a rookie. I have attached my logs. When I tried to create xorg.txt I got a message that it did not exist. I appreciate any help in resolving this. 

Thank you!!!
Paul

---

### Post by The_Autonomist on 2011-10-15
My Firefox keeps crashing as well. Whenever I go to open a new tab, it freezes and then the window turns gray.

I've had to revert back to Chrome due to this.

---

### Post by zasq on 2011-10-15
Hi! I had this problem too. When I started Firefox from the terminal, I could see there was a problem with the gecko-mediaplayer. So, here's what solved the problem for me:

```
sudo apt-get remove --purge gecko-mediaplayer gnome-mplayer
```

After that, I rebooted (just to be sure) and reinstalled both:

```
sudo apt-get install gecko-mediaplayer gnome-mplayer
```

The bug is documented here: [https://bugs.launchpad.net/ubuntu/+source/gecko-mediaplayer/+bug/812053]("https://bugs.launchpad.net/ubuntu/+source/gecko-mediaplayer/+bug/812053")

For some reason, upgrading from natty to oneiric failed to make a "clean" installation of the gecko-mediaplayer.

Good luck!

---

### Post by deeporbit on 2011-10-18
I checked and I didn't have the gecko items installed. I installed those and left the terminal window open. I opened firefox and it crashed right away. The terminal window showed an error for something like unable to find "pixmap" so I installed that. Facebook has stopped crashing using Chromium. However this page, UbuntuForums.org crashes repeatedly using Chromium. Starting to make progress.

---

### Post by deeporbit on 2011-10-18
> **deeporbit said:**
> I checked and I didn't have the gecko items installed. I installed those and left the terminal window open. I opened firefox and it crashed right away. The terminal window showed an error for something like unable to find "pixmap" so I installed that. Facebook has stopped crashing using Chromium. However this page, UbuntuForums.org crashes repeatedly using Chromium. Starting to make progress.

Well, Chromium has crashed a few times after installing gecko-player. Hrm....It's not crashing as bad but still.

---

