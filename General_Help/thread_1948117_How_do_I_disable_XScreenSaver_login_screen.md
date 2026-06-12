---
title: "How do I disable XScreenSaver login screen?"
date: 2012-03-27
forum: General Help
---

### Post by pretty_whistle on 2012-03-27
It's coming up after I close laptop lid and try to resume.

I have Ubuntu 11.04 with Xfce desktop.

---

### Post by pretty_whistle on 2012-03-27
I solved it by uninstalling XScreenSaver.

Don't need it anyway.

---

### Post by ubifree on 2012-07-19
I have the same problem but I don't want to 'solve' it by removing XScreensaver! Does anyone know how to disable the login prompt upon waking from suspend? (I'm using ubuntu 12.04.)

---

### Post by matt_symes on 2012-07-19
Hi

@ubifree

Open the dash and type

```
brightness and lock
```

1. Select the application and turn "Lock" to off position. This wil disable the password prompt when the screen get locked by the screen saver and or the screen is turned off.

2. Uncheck "require my password when waking from suspend". This will disable the password when waking from suspend.

Select the best one for you.

Kind regards

---

### Post by ubifree on 2012-07-22
Thanks for your suggestions Matt. Unfortunately, both those settings you mentioned in Brightness and Lock were already set as you described.  In other words, their values appear to be ignored.

Also, within XScreensaver the checkbox which says 'Lock Screen After 0 minutes' is also unchecked.  I'm using the Electricsheep screensaver in case that's relevant.

Any other ideas?  BTW This never happened in ubuntu 11.10.  It's only happened since I upgraded to 12.04.

---

### Post by ubifree on 2012-07-22
Hmm, I did some more testing.  It looks like I'm not prompted for a password upon resume if I manually suspend the laptop.  So it looks like those Brightness and Lock settings are honoured after all.  However, I am prompted for a password by XScreenSaver if the laptop went to sleep whilst the screensaver was active. So it definitely seems to be an XScreenSaver issue.

---

### Post by kerryhall on 2013-01-28
I'm having the same issue. xscreensaver activates when I close the lid of my laptop. Desired behavior: do not do that :)

---

