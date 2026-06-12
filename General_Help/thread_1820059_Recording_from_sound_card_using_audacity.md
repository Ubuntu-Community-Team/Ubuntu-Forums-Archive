---
title: "Recording from sound card using audacity"
date: 2011-08-07
forum: General Help
---

### Post by cupagreent on 2011-08-07
Hi, I'm using a dell inspiron 15r laptop, after following several tutorials I am still unable to record the sound directly from my soundcard's output.

Any ideas or suggestions?

---

### Post by SalHelder on 2011-08-07
Have you tried to go to Sound Preferences? It's on System > Preferences > Sound. And then check the Input tab, and select the correct input device from the list, that should do it in most cases.

---

### Post by cupagreent on 2011-08-07
There is no input devices

---

### Post by SalHelder on 2011-08-07
Oh, sorry... I misread, you are trying to record from the output. It's normal that there is not input there. I also used to have similar problems in the past, right now I've tested and while running mpg321 (to play mp3 trough the console) audacity does record the output without any input devices.

Try to make sure if audacity is recording from ALSA or PulseAudio, since it should have the same settings you have on the output.

The only option I found that you might not have on in audacity is the overdub.

---

### Post by cupagreent on 2011-08-07
Hmm ...
 
I have managed to get it to record by routing the sound to the hdmi out port .. however this removes speaker functionality as I cannot seem to get audacity to recognise (or even find) my regular speaker output

---

### Post by SalHelder on 2011-08-07
I'm pretty sure that under ALSA this should work just fine, which is odd. First try to use another software to see what happens, for instance Jokosher.

Try typing in the console:
gstreamer-properties

And change first the input to ALSA, to see if it works now.

---

### Post by cupagreent on 2011-08-08
after some mucking around with a few things , I got it to work using an audio splitter and a double ended audio jack cable linking my headphone socket to my line in socket , and hey presto it works 

thanks for your suggestions

---

