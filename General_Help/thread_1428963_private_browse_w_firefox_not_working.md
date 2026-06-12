---
title: "private browse w/ firefox not working"
date: 2010-03-13
forum: General Help
---

### Post by collinge on 2010-03-13
It used to work... now when u click on private browse, nothing happens. Do i need to update or something.... if so whats the code for terminal. thanks

---

### Post by akakingess on 2010-03-13
I am a little ignorant on the subject of "private browse", so could you please explain what you mean by that? Also, to launch firefox from the terminal, you just need to open the terminal and type in firefox, or maybe firefox-3.5, depending on which version you are running.

---

### Post by collinge on 2010-03-13
Private Browse is a mode in firefox 3.5 that doent save any information about your session.. i am currently using firefox 3.5.8. Launching firefox is not  the issue. i guess updating or down grading?

---

### Post by uRock on 2010-03-13
When you click Start Private Browsing, you don't go to this page?

---

### Post by uRock on 2010-03-13
> **collinge said:**
> Private Browse is a mode in firefox 3.5 that doent save any information about your session.. i am currently using firefox 3.5.8. Launching firefox is the the issue. i guess updating or down grading?

I am using the same version and it works without any problems

---

### Post by collinge on 2010-03-13
no... nothing happens... i even press ctrl+shift+p ... restarts dont work.

---

### Post by uRock on 2010-03-13
You should try uninstalling Firefox, then reinstalling it. That issue is odd, but I think a reinstall should fix it. When you reinstall you will not loose your bookmarks and such.
I would recommend uninstalling via Synaptic, then run this command, ```
sudo apt-get autoremove
``` then reinstalling via Synaptic.

---

### Post by lovinglinux on 2010-03-13
See the Troubleshooting section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by pj_kare on 2010-04-06
I have the same problem, and I un-installed and re-installed a dozen times, each time trying to find more firefox stuff to delete.
I gave up and did a format and re-install.
In 3.5.3 private browsing worked fine, after updating to 3.5.8 it stopped working.

Error console reports this each time I try to start Private Browsing:

```
Exception thrown while processing the private browsing mode change request: [Exception... "Could not convert JavaScript argument arg 0 [nsISupports.QueryInterface]"  nsresult: "0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS)"  location: "JS frame :: file:///usr/lib/firefox-3.5.8/components/nsPrivateBrowsingService.js :: PBS__ensureCanCloseWindows :: line 247"  data: no]
Source File: file:///usr/lib/firefox-3.5.8/components/nsPrivateBrowsingService.js
Line: 375
```A google search on this error reveals that it was a bug posted last year.

---

### Post by pj_kare on 2010-04-06
Just as well I needed a clean install of Karmic ( I've done a lot of messin' about trying to learn ). It appears I didn't need to re-install, all I needed to do was update to the latest xulrunnner-1.9.1 ( Picked the one in synaptic that was already installed to update, as there is so many listings for xulrunner ). 

All now working, though I had a bit of trouble shutting down and restarting Firefox, it was closed but still running and I had to open System Monitor and -End Process-

---

