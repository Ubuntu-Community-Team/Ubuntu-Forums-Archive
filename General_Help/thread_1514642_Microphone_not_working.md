---
title: "Microphone not working"
date: 2010-06-21
forum: General Help
---

### Post by CoolJohnB on 2010-06-21
I have a Dell Vostro 1700 laptop and have recently installed Ubuntu 10.4 with the help of this forum I have been able to get everything working well except the microphone.  I have been to System>preferences>sound and found the mic was muted having taken the tick out of that box it still doesn't work!  Any suggestions?  I particularly want to use it with Skype.

Any help would be much appreciated.

---

### Post by eigenein on 2010-06-21
Try to increase Input volume slider and/or select appropriate Connector for your microphone.

---

### Post by CoolJohnB on 2010-06-21
I have tried increasing input volume and it had no effect, the microphones are built into the lid of the laptop, either side of the web cam, the software recognizes them as being there, but they don't work.

---

### Post by CoolJohnB on 2010-06-21
I wonder if it might be something to do with the sound driver as it is shown as a duplex analog device with 1 input and 1 output but there are 2 inputs the built in mic's plus a jack for an external mic, or does that all go to one input? as of course there's the same for the output and they both work fine.

---

### Post by 4chan on 2010-06-21
i have the same issue with you. try this on terminal:

***gstreamer-properties***

and change default input to ALSA.

it works for me and i hope it will works for you also.

---

### Post by CoolJohnB on 2010-06-21
Thanks for the suggestion, tried all options from drop down list but sadly none of them work!  Any other suggestions?

---

### Post by 4chan on 2010-06-21
i'm sorry i can't help you much with this issue because the step i mention b4 working for me and i'm still newbie myself.
but keep asking there must be someone who knows how to fix the issue.

---

### Post by CoolJohnB on 2010-06-21
Thank you for your suggestions, it is now getting weirder!  I plugged in a USB webcam with built in microphone it works but on playback sounds like Chinese!  Anyone got any ideas?

---

### Post by vangop on 2010-07-31
I was fighting with internal mic on 8.04 and somehow got it to work, but the volume was very low.
After installing 10.04 I can't get it to work at all.
Add compiz incompatibility with intel 965 graphics and I start to hate this piece of dell.
There's a tip that might help, my mic is again very quiet but works. [here]("http://wwww.ubuntuforums.org/showpost.php?p=9597080&postcount=5")

---

### Post by T_038 on 2010-07-31
GIAT (give it a try):

left-click on the sound icon, sound preferences > tab: output, select the one you want. Or, down there, click on the connector drop-down and select analog headphones for example.

---

### Post by vangop on 2010-08-01
Didn't help me, still my int mic is too quiet.
Sound system is a mess on ubuntu, there's like 5 places where you can config it (or break) - alsamixer, pulseaudio volume, regular sound preferences, padevchooser, gstreamer..

---

### Post by T_038 on 2010-08-01
Did you went to alsamixer to check the volume level, after following my post's guide?

---

### Post by deputyjones on 2010-08-21
> **vangop said:**
> I was fighting with internal mic on 8.04 and somehow got it to work, but the volume was very low.
After installing 10.04 I can't get it to work at all.
Add compiz incompatibility with intel 965 graphics and I start to hate this piece of dell.
There's a tip that might help, my mic is again very quiet but works. [here]("http://wwww.ubuntuforums.org/showpost.php?p=9597080&postcount=5")

This fixed it for me, thanks.

---

### Post by vangop on 2010-08-23
ok, internal mic no longer quiet :)
HOWTO:
1. install padevchooser
2. in the manager, open Devices tab, then under Sources tree find your mic (there are 2 of them, monitor and Internal Audio .. - select the latter).
3. Click properties and drag the volume scrollbar to the right over 100%. I even didn't pull it to the max and the volume was great.

Hope that helps somebody.

---

### Post by vanlindholm on 2011-03-07
installing the alsa driver modules fixed this for me... note restart is required

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

---

