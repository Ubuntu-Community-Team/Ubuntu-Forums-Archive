---
title: "ubuntu 9.10 on asus 900a very low audio input level"
date: 2009-11-22
forum: General Help
---

### Post by natholas on 2009-11-22
hi, i have been looking around google for a while now and i cant find anyone that can help me.. i have an asus 900a which has a hda intel sound card, i am running ubuntu netbook remix (up to date)

i used to have eeebuntu on here and the audio recording was really bad (hissing) and it was really really annoying so when i saw that karmic had come out i thought that i would give it a try. when i installed it the audio capture was reasonably good! it was a bit low but allot better than eeebuntu. but now after not messing with anything i was skyping a friend and she said that she could hardly hear me because my audio was very low and had a buz in it.. i was suprised and thought it was on her end but i tried the audio recorder and it was very low and had a buz.. this is really frustrating.. anyone have any ideas?

(i tried running alsamixer in the command line and it looks normal)
(imput level is on the line (unamplified) where i worked fine before)
thank you in advanced

---

### Post by natholas on 2009-11-22
oh and i havent changed any of the programs controlling my audio settings

---

### Post by Sven6210 on 2009-11-23
I had the same issue already with Ubuntu 9.04 and part of the patch I did for 9.04 is also necessary in Ubuntu 9.10 (see [http://ubuntuforums.org/showthread.php?t=1289061](http://ubuntuforums.org/showthread.php?t=1289061))

**Patching of the ALSA configuration file (/etc/modprobe.d/alsa-base.conf)**

1. Open a terminal window
2. Enter 'sudo gedit /etc/modprobe.d/alsa-base.conf'
3. Search in the file whether a line including 'snd-hda-intel' exists, if so please delete that line
4. Add the following two lines to the configuration file:

===start here===
# eeePC 900a patch
options snd-hda-intel index=0 model=quanta
===end here===

5. Save the ALSA configuration file and close the editor (gedit)



I hope this works for you - on my 900a I have Ekiga (for SIP based VoIP) and Skype running.

---

### Post by natholas on 2009-11-25
Dude! thanks allot for taking the time to post that :) my audio recording is perfect now! ahhhhhhh that made my day!

---

