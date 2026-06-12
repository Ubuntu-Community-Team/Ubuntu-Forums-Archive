---
title: "Resume from suspend - no password?"
date: 2011-12-31
forum: General Help
---

### Post by Roasted on 2011-12-31
Is there a way to resume from suspend that allows me to just be presented with my desktop instead of having it with a password box? 

Thanks!

---

### Post by guestolo on 2011-12-31
Assuming your using Ubuntu 11.10

1. First try the Lock/Unlock button in System Settings -> Personal -> Screen
That doesn't work for me

2. In terminal do the following
```
gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'
```
that works for me
More info
[http://ubuntuforums.org/showthread.php?t=1466504](http://ubuntuforums.org/showthread.php?t=1466504)

---

### Post by Anthony A on 2011-12-31
I was going to post asking the same thing. My situation is a little different. If I suspend by closing the laptop lid then I have to enter my password when resuming. If I suspend by using the suspend option in the menu then I don't have to enter a password when resuming.

---

