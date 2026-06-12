---
title: "Google Chrome after update"
date: 2012-07-12
forum: General Help
---

### Post by pottzie on 2012-07-12
I had some problems with Google Chrome a few days ago.[http://ubuntuforums.org/showthread.php?t=2021652&highlight=chrome+chromium](http://ubuntuforums.org/showthread.php?t=2021652&highlight=chrome+chromium)

 The "fix" was either google-chrome --disable-bundled-ppapi-flash
or 

 mv /opt/google/chrome/PepperFlash /opt/google/chrome/PepperFlash.bak google-chrome

 I ran both commands just so I could get Chrome to open and run, but it made Chrome work only if I gave up video. The internet without video is kinda funky, and since I see Google has updated Chrome, is there any way I can get the new Chrome and video working?

---

### Post by Pilot6 on 2012-07-12
You disabled bundled flash. You need yo install external flash, if it was not installed before.

sudo apt-get install flashplugin-installer

---

### Post by pottzie on 2012-07-12
No, I've installed flash.
```

flashplugin-installer is already the newest version.


```

---

