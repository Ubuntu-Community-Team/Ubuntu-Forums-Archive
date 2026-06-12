---
title: "Playing Music without a mic?"
date: 2011-09-11
forum: General Help
---

### Post by Buckstabu on 2011-09-11
Okay, So I used to do this thing in windows, where you go into sound options, and change a setting so that whatever comes from my speakers, people here.

Is it possible to do this in ubuntu? I can't seem to do it.

^Noob to ubuntu, Please give me a step-by-step if possible

---

### Post by boblizar on 2011-09-11
ok its going to be done in a few steps

ctrl + f2

enter

gksu synaptic

then run

enter your root password

find and install qjackctl

alt + f2

enter

qjackctl

run

configure the settings for your sound device for in and out playback stuff

then turn jackd on by pressing play, then load the connections tab, and connect stereo in to stereo out and it effectively makes a "mic to speaker" connection...

---

### Post by Buckstabu on 2011-09-11
Okay, I figured all of that out, up to one point, When I link stereo in to stereo out... What do I link? All I have is tons of "Playback_1" through "Playback_6" and then it says "Capture_1" on the other side

---

### Post by pqwoerituytrueiwoq on 2011-09-11
simple command line version of what he said 
```
sudo apt-get install qjackctl;qjackctl;
```
open terminal copy paste press enter type pass and you are done

---

