---
title: "How to enable system tray icons"
date: 2011-07-23
forum: General Help
---

### Post by don762003 on 2011-07-23
Is there a way to enable the system tray to display the icons for running apps in the unity panel like they did in the old gnome ubuntu? For example Pandora.

---

### Post by Rasa1111 on 2011-07-23
[http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html](http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html)

> **To enable the Notification Area (Systray) for all applications**, run the following command:
```

gsettings set com.canonical.Unity.Panel systray-whitelist "['all']" 
```

> **Once you run the command, log out and then log back in.**

works perfectly here. :)

---

### Post by mikejonesey on 2011-07-23
think there is a generic app called all tray or something along those lines that is capable of adding any app to the system tray...

---

### Post by don762003 on 2011-07-24
Thanks for the tips. I also found a way to do it using a gui. [www.ubutip.blogspot.com](www.ubutip.blogspot.com)

---

### Post by Rasa1111 on 2011-07-24
no problem.
I find the single command soo much easier/nicer than having to install something else just to whitelist apps though! 
Cool that it exists for whoever needs it though.

---

