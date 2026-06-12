---
title: "Log-in Sound Disappeared"
date: 2009-11-24
forum: General Help
---

### Post by ChappyHappy on 2009-11-24
Running 9.10.

There's two login sounds that plays which I've experienced after the initial install.
1-the short one that plays when it notifies me that I can choose and user and enter the pw
2-the longer one that plays after entering the pw and right before loading the desktop

For me, sound#1 still plays but sound#2 stopped playing after I did something.
Unfortunately, I dont know exactly what I installed/editted that caused this.

Thanks in advance.

Also, another unrelated problem I just experienced is that I was unable to create this thread with firefox but was able to in chrome...

---

### Post by Yellow Pasque on 2009-11-24
Is the startup sound still set to play in System -> Preferences -> Startup Apps ?

---

### Post by ChappyHappy on 2009-11-24
Yes, I forgot to mention that in my original post.

---

### Post by Yellow Pasque on 2009-11-24
Try playing "sound #2" in the terminal:
```
canberra-gtk-play --file=/usr/share/sounds/ubuntu/stereo/desktop-login.ogg
```

---

### Post by ChappyHappy on 2009-12-01
Ok, I have a feeling that was suppose to play a sound after hitting enter.

There's a pause (not the program freeze pause, pause as in the cursor just blinks by itself in a new line, and there's no user@user-laptop: prefix) in the terminal.

Sorry for the late reply, I had work to do the past week.

---

### Post by Yellow Pasque on 2009-12-01
Do you have the libcanberra-pulse package installed?

---

### Post by fluffman86 on 2009-12-01
I hate to ask this...but are your speakers muted?  Check the sound icon next to the clock, and maybe run alsamixer in a terminal.  

Karmic has a bug where sometimes when you login you're automatically muted.  Which would make sense since your sound plays when you aren't logged in (the ready drums), but doesn't play when you you're loading your user profile.

---

### Post by slamhound on 2009-12-01
Another thing to check would be the Alert Volume under Sound Preferences (Under System->Preferences).  I had the same problem as you (strangely only happened on one of two new installs on identical hardware).  I also had the pause when running canberra-gtk play.  Turns out it was playing the sound, I just couldn't hear it.  Other sounds on the system worked fine and were at an appropriate volume, and the Alert Volume had been set at about half, so I initially thought that couldn't be it.  But when I turned the Alert Volume slider up to 100% volume, I had all my alert sounds (including the login sound).

---

### Post by ChappyHappy on 2009-12-01
@ Temujin
Yea, I have the package installed. Reinstalled it anyways.

@fluffman
Nope, nothing is muted upon login as I dont have to adjust volume to hear anything.

@slamhound
Silly me. lol. I probably was playing around with some settings and turned the Alert Volume down to around 20%. Brought it back up to 100% and problem solved.

Thank you everyone for your help!

---

