---
title: "sound in flash is wierd"
date: 2006-06-13
forum: General Help
---

### Post by Polygon on 2006-06-13
whenever i watch flash movies or something (like in newgrounds), when there seems to be a lot of action, the sound and movie slows down and the sound starts to get distorted a bit, and gets kind of "crackly".

i had ubuntu autoconfigure my sound card, which is a soundblaster live 24 bit

is there anyway to fix this?

---

### Post by givré on 2006-06-13
Did you try that [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
Search for "flash issues"

---

### Post by Polygon on 2006-06-13
> Install alsa-oss package.

Open:

    *

      sudo nano /etc/firefox/firefoxrc 
        

Add/Change line:

    *

        FIREFOX_DSP="aoss"
        

*Restart FireFox, and try the page again.

If the above does not work, try the following:

Open:

    *

      sudo nano ~/.mozilla/firefox/rc 
        

Add the line:

    *

        FIREFOX_DSP="none"
        




i did that now i get NO sound at all in flash, and even when reversing all of that i still get no sound....

---

### Post by ograndedienne on 2006-06-13
do you have dma active on disks ?

---

### Post by givré on 2006-06-13
Try to launch firefox without sound from any of your applications, and launch your flash. If there is no sound, i don't really know what is the problem.

---

### Post by Polygon on 2006-06-14
well, after a restart sound is back in flash, but i still have that weird sound slowing down/distortion problem :D

and ogrand, unless that is turned on by defualt, i do not that have enabled, as i dont even know what that is.

still open to discussion ;)

---

### Post by sugonaut on 2006-06-14
This worked for me, Polygon.

[http://www.ubuntuforums.org/showpost.php?p=1138486&postcount=11](http://www.ubuntuforums.org/showpost.php?p=1138486&postcount=11)

---

