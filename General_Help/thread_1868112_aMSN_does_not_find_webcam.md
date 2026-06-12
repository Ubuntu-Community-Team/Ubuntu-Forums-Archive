---
title: "aMSN does not find webcam"
date: 2011-10-23
forum: General Help
---

### Post by BSG Fan on 2011-10-23
When I start the Assistant to setup the webcam, it says that no webcam has beeen found, or the webcam is already in use by another program (I guess is Skype).

Okay, later I went to [http://amsn.sourceforge.net/devwiki/tiki-index.php?page=Webcam+In+aMSN#webcamsn](http://amsn.sourceforge.net/devwiki/tiki-index.php?page=Webcam+In+aMSN#webcamsn) to check the options to solve the problem but I can not identify how fix the situation.

Somebody here can toss some light?

thanks in advance

:)

---

### Post by no2498 on 2011-10-24
look in your system/preferences auto startup programs 
you need to turn them off things like cheese skype msn flash
then restart the computer

---

### Post by honeybear on 2011-10-24
> **no2498 said:**
> look in your system/preferences auto startup programs 
you need to turn them off things like cheese skype msn flash
then restart the computer

ls /dev/video*

does it play usnig mplayer? 
mplayer tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video0.

---

