---
title: "No login sound"
date: 2010-08-07
forum: General Help
---

### Post by Winalways on 2010-08-07
I hear no login sound when I login to my ubuntu. I checked at startup applications and found GNOME login sound is enabled. The command used there is 
```
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
```.

Its not only this, but there is no other sounds enabled - for mouse clicks etc.

Thanks in advance!

---

### Post by Revolutionary101 on 2010-08-07
Go to System>Preferences>Sound. When that window shows up make sure that Ubuntu is selected for sound theme.

---

### Post by Unknown-Demon on 2010-08-07
I've had a similar issue with no sound at login and mouse clicks and videos.
I was looking around to see if I can find an issue and everything worked fine.
I continued to look on Google and I found a solution that fixed my issue.
Go to terminal and type the following;
```
alsamixer
```
and be sure nothings muted.

---

### Post by Winalways on 2010-08-08
> **Revolutionary101 said:**
> Go to System>Preferences>Sound. When that window shows up make sure that Ubuntu is selected for sound theme.

Thank you! Now its alright. Though the sound theme was ubuntu, the alert volume was set to almost zero. That was the reason.

---

