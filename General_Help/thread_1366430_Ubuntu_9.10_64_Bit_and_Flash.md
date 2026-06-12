---
title: "Ubuntu 9.10 64 Bit and Flash"
date: 2009-12-28
forum: General Help
---

### Post by Nemo0075 on 2009-12-28
Hi Guy's

  I have been using 64 Bit Ubuntu since 9.04 and all is well except for adobe 64 bit flash.  I have just been living with problem and adjusting my usage to least aggravate the situation.  I actually had it working 100% just briefly after installing 9.10 but an upgrade buggered it up and I can't recall how I had fixed it.  Here is what I have been living with:

Start up Firefox go to Youtube, everything is fine.  Surf over to another site with flash videos, click on video and get a white screen.  Go back to Youtube and click on videos, get white screen.  Shut down Firefox, start it up again and repeat.

  I have tried many of the fixes I have found with little to no long lasting success.  Any ideas?

  Thanks once again for all the help.

---

### Post by RobLikesBrunch on 2009-12-28
Uninstall your current install, and try:

```
sudo apt-get install flashplugin-nonfree
```

The white-screen bit happens to me occasionally...but not nearly as often as you describe. I still have problems interacting with certain flash applications (can't adjust volume, etc).

---

### Post by Nemo0075 on 2009-12-28
> **RobLikesBrunch said:**
> Uninstall your current install, and try:

```
sudo apt-get install flashplugin-nonfree
```

The white-screen bit happens to me occasionally...but not nearly as often as you describe. I still have problems interacting with certain flash applications (can't adjust volume, etc).

Been there done that.  I just tried it again to throw caution at the wind.  Same problem.  Just to be clear, this is not an intermittent problem.  This happens every time.

---

### Post by oldos2er on 2009-12-28
If you installed 32-bit flash (which the command sudo apt-get install flashplugin-nonfree will do), you need to uninstall it before installing 64-bit flash.

See [http://www.myscienceisbetter.info/install-native-64bit-flash-player-10-on-linux.html](http://www.myscienceisbetter.info/install-native-64bit-flash-player-10-on-linux.html)

---

