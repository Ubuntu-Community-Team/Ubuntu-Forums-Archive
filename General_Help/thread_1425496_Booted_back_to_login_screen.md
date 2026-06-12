---
title: "Booted back to login screen"
date: 2010-03-09
forum: General Help
---

### Post by G-Fru on 2010-03-09
Hi, i'm a new user, and I can't find any resolution to the problem i am facing.

When i installed (10.04) i set my user to have auto login. When I turned on my machine i get through to the desktop, at which point i can navigate everywhere and open any program etc. but as soon as i press the enter key (i tried pressing every other key to make sure) i get booted back to the main login screen and have to put in my password to login. When i log i get taken back to a desktop with everything that i did previously is gone.

This problem follows another problem where i would be taken to the desktop but would be prevented from doing anything by a prompt that asked for a keyring password, where by when hitting the 2 (i tried pressing every other key to make sure) button i would be booted back to the login in screen. I followed the advice of another forum that suggested it was due to my wireless networking settings which i have now set to allow all users and that no longer happens.

Anyone have any ideas?

---

### Post by cong06 on 2010-03-09
I just posted a similar problem I've been having: [http://ubuntuforums.org/showthread.php?t=1425386](http://ubuntuforums.org/showthread.php?t=1425386)
My version is 9.04...

Just out of curiosity, could you cause it to happen and then check the /var/log/syslog file to see if you have a similar entry?
Maybe try this:
```

tail -400 /var/log/syslog

```
to see the last 400 lines (for me it was about this far... maybe more...)
This log fills up though.

This is weird.

---

