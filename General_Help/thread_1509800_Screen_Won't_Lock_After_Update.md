---
title: "Screen Won't Lock After Update"
date: 2010-06-14
forum: General Help
---

### Post by GrantStoner on 2010-06-14
Basically the title says it all. After selecting software sources and doing the updates, my screen won't lock. Directly after I install Ubuntu, I can use BOTH the shortcut (Ctrl+Alt+L) and manually click "Lock Screen" and it will take me to the lock screen. However, after I install the updates and reboot, I cannot lock my screen either way. Is there a workaround for this? Or a way to fix it? I love my lock screen... I feel less secure without it!

---

### Post by rjs987 on 2010-09-27
I am still on Kubuntu 9.10 and just started having this same issue. I have the widget for screen lock on my desktop and after installing the latest 6 updates this morning found that the widget didn't work. Then I tried other means of locking the screen and nothing happens with any. Have not had any problems with this until today.

---

### Post by GrantStoner on 2010-09-27
Did you change any of the default startup applications? If you did - go back and see if the screensaver box is checked. I found this to be my problem. As soon as I re-enabled the screensaver on startup applications, it worked no problem.

---

### Post by rjs987 on 2010-09-28
Screen saver is enabled. Was not ever disabled so I did disable it and then re-enabled it to apply the setting again. Still no screen lock.

---

### Post by GrantStoner on 2010-09-28
I'm not sure what screensaver daemon KDE uses by default (although I should - as I'm using Back|Track now ^_^) but if it's not xscreensaver, then ```
sudo apt-get remove "current-screensaver"
sudo apt-get install xscreensaver
``` if you're using the xscreensaver already, then try installing the gnome-screensaver```
sudo apt-get install gnome-screensaver
```

---

### Post by rjs987 on 2010-09-28
thanks, I'll try that tomorrow. The problem is on my work computer. My home computer is working fine. KDE can use kscreensaver or xscreensaver so I will try one of those.

---

### Post by rjs987 on 2010-09-29
Attempted to remove the current screensaver but not sure of which one was installed. During the second guess I was reminded that there were packages not needed and should be autoremoved so I did that next then, on a whim, I tried the screen lock and it is working today. Thanks again for the suggestions. I may yet install Kscreensaver since that doesn't require an additional package to work in KDE and will also use xscreensaver graphics.

---

### Post by GrantStoner on 2010-09-29
Glad to help. ^_^

---

