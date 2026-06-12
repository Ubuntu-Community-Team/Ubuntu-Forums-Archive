---
title: "Some noob questions"
date: 2009-07-21
forum: General Help
---

### Post by YasirMX on 2009-07-21
How do I:

1) Get admin privileges in konqueror to copy a file to /root folder?
2) Enable my internal richo card reader which is disabled on my dv6000 laptop?
3) Get my MIC working correctly on skype?? 

For the third one, I've been striving a lot and people can't hear me on skype :( :confused:

---

### Post by Sxeptomaniac on 2009-07-21
In a terminal, the command: ```
kdesudo konqueror
``` should be able to let you use it in admin mode.  I'll look into the other questions and get back to you, unless someone beats me to it.

Edit:  It appears the mic problem isn't new.  There's a fix in [this thread in post #9](http://ubuntuforums.org/showthread.php?t=1039685).

---

### Post by Codix121 on 2009-07-21
With your 3rd question,
What mic are you using?

---

### Post by Codix121 on 2009-07-21
Oh sorry thought you said CAM, my bad,
for the mic try going to your sound options

go to terminal and type in:

```
gnome-sound-properties
```

check your INPUT and see if your mic is turned up.
Also check your volume control,
In terminal type:

```
gnome-volume-control
```
Make sure your mic volume is up all the day,
by default on my PC it's all the way down.

---

### Post by Sxeptomaniac on 2009-07-21
I believe this user is on Kubuntu, so ```
kmix
``` or ```
alsamixer
``` would probably be better for checking sound levels

---

