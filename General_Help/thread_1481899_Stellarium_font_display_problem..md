---
title: "Stellarium font display problem."
date: 2010-05-13
forum: General Help
---

### Post by WarrenL on 2010-05-13
Hi folks,

Since upgrading to Lucid I've had the following problem with the display of the "selected object information" in Stellarium:

[IMG]http://i212.photobucket.com/albums/cc10/bogchook/Posts/Screenshot-Stellarium0104-1.png[/IMG]

Often the correct text very briefly displays when you click on an object before going all scrambled as in the picture.

I don't imagine for a moment that I'm the only one to have had this problem, so do any of you know what's happening?

---

### Post by daggerstab on 2010-05-13
[https://bugs.launchpad.net/stellarium/+bug/525995](https://bugs.launchpad.net/stellarium/+bug/525995)

Open ~/.stellarium/config.ini and add under "[main]" the following two lines:
```
use_glshaders = false
use_qpaintenginegl2 = false
```If you feel comfortable enough compiling something from source, you may be able to help Fabien locate the problem.

---

### Post by WarrenL on 2010-05-15
Thanks, daggerstab! That nailed it. I would never have figured that out for myself...

Sorry for the slow reply - I was away from the computer for a couple of days.

---

### Post by daggerstab on 2010-05-15
And I'm sorry about the typo in the path - it should be "~/.stellarium/config.ini". I assume "That nailed it." means that you have managed to find the proper file?

---

### Post by WarrenL on 2010-05-27
Sorry daggerstab, I'd lost track of this thread. Yes indeed, I'd guessed the correct path to the file and now everything is OK. I appreciate your help - my 6-year-old son is star crazy and a malfunctioning Stellarium was causing him no end of distress.

---

### Post by Paul Bramscher on 2010-07-12
Thanks for the fix!  I encountered the same issue on my older PC (circa 2005, using the proprietary Nvidia drivers with Ubuntu 10.04).  Didn't have this problem with 8.04.

I'd like to add that in addition to definitely solving this bug, the fps (frames per second) rate radically improved.  Prior to issuing the fix, I believe it was around 4-10 fps.  After the fix, it was a far smoother ~30+ fps.

> **daggerstab said:**
> [https://bugs.launchpad.net/stellarium/+bug/525995](https://bugs.launchpad.net/stellarium/+bug/525995)

Open ~/.stellarium/config.ini and add under "[main]" the following two lines:
```
use_glshaders = false
use_qpaintenginegl2 = false
```If you feel comfortable enough compiling something from source, you may be able to help Fabien locate the problem.

---

