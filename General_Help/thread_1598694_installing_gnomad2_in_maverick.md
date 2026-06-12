---
title: "installing gnomad2 in maverick"
date: 2010-10-16
forum: General Help
---

### Post by onemanclapping on 2010-10-16
Hey!

I installed maverick and noticed they don't include "gnomad2" package at the "regular" apt-get packages anymore.

What can I do in order to "add" the old repository again? I really need this program and the website version includes some really old instructions which do not work under this new linux... :S

Thanks in advance.

---

### Post by onemanclapping on 2010-10-17
C'mon, don't make me install the old Ubuntu on a pen drive just to extract a recording from my Jukebox 3! :P

---

### Post by MissEileen on 2010-11-27
same problem here :(

---

### Post by sam_i on 2010-11-29
Same here - don't tell me Ubuntu isn't supporting this device anymore? Why that would be just like M$... oh except they do on windows 7!

Windows 1, Ubuntu 10.10 0? common this has to be a Fail!

Any suggestions out there?

---

### Post by sam_i on 2010-11-30
Ok having a play around means somehow everything now works in rhythm box, which is as I wanted it anyway. Also the Zen drive now appears on the desktop when connecting.

The only specific things I thought that changed this was plugging in a few times and then rebooting the machine with the Zen drive still plugged in. 
The only other thing I did was possibly update the mtp version to v8 (see code below) however I believe this is installed by default so may be a red-herring.

Can other poster'ers please try the restart approach as above and let us know of the results - perhaps they do nothing!

```
apt-get install libmtp8
```

---

### Post by gnimsh on 2010-12-13
There no longer seems to be a way to manage playlists though. Have you had any luck with that?

---

### Post by onemanclapping on 2011-02-15
solution!!! yaaaay

[http://ubuntuforums.org/showpost.php?p=9994733&postcount=7](http://ubuntuforums.org/showpost.php?p=9994733&postcount=7)

---

### Post by cybersuneel on 2011-02-16
> **onemanclapping said:**
> solution!!! yaaaay

[http://ubuntuforums.org/showpost.php?p=9994733&postcount=7](http://ubuntuforums.org/showpost.php?p=9994733&postcount=7)
Nice solution!  gnomad2 now works, but both amarok and rhythmbox crash (with a segmentation fault) on seeing my Creative Zen Mosaic on the USB bus.  Any clues anyone??

---

