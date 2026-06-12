---
title: "Ubuntu 11.04 - Unity not working"
date: 2011-09-23
forum: General Help
---

### Post by MannheimRocket on 2011-09-23
I've been using Ubuntu 10.10 for quite some time now, and finally decided it was time to upgrade to 11.04. However, upon logging into Unity after the upgrade, the desktop was blank with nothing showing up except my mouse and the wallpaper. I can log in to Ubuntu classic, which is what I'm using now. I'm fairly new to ubuntu, and I don't know how to fix this, or if it can be fixed. My graphics card is an ATI RadeonTM Xpress 1200. 

Sorry if I'm posting in the wrong category, I'm new here!;)

---

### Post by garvinrick4 on 2011-09-23
Try this in terminal:
```
unity --reset 
```If not go to Ubuntu software Center and put CCSM in search window
and install.
Open:
```
ccsm
```Make sure unity plugin is checked.
Do not mess with anyother settings in CCSM or you will have a failure.
Might have to log out and back in not in Unity right now.

This code will tell you if your machine is 3d capable.
```
/usr/lib/nux/unity_support_test -p
```If Unity interface does not come up then it is time to see about graphics drivers:
I myself have not had a Unity problem in quite some time in 11.04 but then I have Vanilla cards with kernel drivers.

---

### Post by MannheimRocket on 2011-09-23
Well, that was easier than I thought. Unity seems to be working fine now. Thanks a bunch!

---

### Post by garvinrick4 on 2011-09-23
> **MannheimRocket said:**
> Well, that was easier than I thought. Unity seems to be working fine now. Thanks a bunch!You are welcome, most of 11.04 has been worked out and pretty darn smooth and will be a imagine until it is no longer supported.
Enjoy Your Ubuntu, MannheimRocket and welcome to the Ubuntu Forums.

---

