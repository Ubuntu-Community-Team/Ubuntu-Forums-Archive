---
title: "unable to open output pipe to /dev/xconsole"
date: 2012-09-08
forum: General Help
---

### Post by Phoenix_Swelter on 2012-09-08
I was running a KDE session and attempted to open the chromium-browser. I got an error message that it couldn't connect to a socket, and to avoid corrupting the user configuration files, the browser was closing. So I closed everything down and rebooted. I got my normal Kubuntu splash screen, but just as the cursor switched to the revolving dotted circle, it dropped me to the shell login. I checked the log and found the entry "Could not create output pipe to /dev/xconsole"

Any ideas or suggestions?

Update: I went to the recovery mode and attempted to restart X. It returned errors that were not in the normal Xorg.0.log.

I am seeing the following:

(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument

I get a huge list of this error before Xinit loses connection with the Xserver. Help!

---

### Post by Phoenix_Swelter on 2012-09-09
Well, gee - do you think it might help if I were to have disk space left on my root partition? :rolleyes:

---

