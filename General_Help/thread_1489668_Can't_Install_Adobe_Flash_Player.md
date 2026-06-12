---
title: "Can't Install Adobe Flash Player"
date: 2010-05-21
forum: General Help
---

### Post by Cubhicbu on 2010-05-21
I am running Ubuntu 10.04 I installed Ubuntu Restricted Extras, and I went on YouTube. Although I can view the video, I can't click on pause, the volume controls, or seek through the video, or put it into fullscreen mode. I went into the Software Center and searched "Adobe Flash Player", and it came up with Adobe Flash Plugin 10. It doesn't have an "install" button on it, so I double-clicked it, and it said " Sorry, 'Adobe Flash Plugin 10' is not available for this type of computer (amd64)."

Is there a way to fix this?

---

### Post by krishnandu.sarkar on 2010-05-21
Try downloading and installing from this link => [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by cogier on 2010-05-21
I get Flash from here [http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/"). It might be worth a try.

---

### Post by sandyd on 2010-05-21
see my signature. download the 64-bit version for Ubuntu.

---

### Post by Cubhicbu on 2010-05-21
Which one do I download? Apt doesn't seem to work.

---

### Post by Cubhicbu on 2010-05-21
That's it! Screw it! I"m going back to Windows! So much less hassle than Linux. 

I'll be back when people start realizing Linux's potential!

---

### Post by wojox on 2010-05-21
Use carlee's application [http://ubuntuforums.org/showthread.php?t=1414595](http://ubuntuforums.org/showthread.php?t=1414595)

You need 64 bit more than likely to get it to play nice.

---

### Post by nushoin on 2010-05-23
open a terminal, then (copy and paste the following two lines into the terminal, then press enter).

# copy from here
sudo apt-get purge adobe-flashplugin flashplugin-installer
sudo apt-get install flashplugin-installer
# to here


answer 'yes' to all questions.
good luck.

---

### Post by wojox on 2010-05-23
Try this for Flash [http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

---

### Post by inso_741 on 2010-05-24
leave it guyz....I guess he is long gone....for good!!!

---

