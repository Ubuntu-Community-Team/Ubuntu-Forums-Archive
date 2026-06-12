---
title: "Sound not working?"
date: 2010-02-24
forum: General Help
---

### Post by johnnytwohats on 2010-02-24
Im running kubuntu 910 on a Dell Dimension E520. Sound has been working fine now no sound works. (Youtube, media player, mixer). Device listed in my Multimedia settings:
HDA Intel (STAC92xx Analog)

Please help. Thanks in advance.

---

### Post by gradinaruvasile on 2010-02-24
Open a terminal, type:

alsamixer

and enter. Make sure the PCM is at 100 or so.

---

### Post by johnnytwohats on 2010-02-24
still doesnt work. like my speakers, headphones, programs, no sound comes out. I think it has to do with my sound card. It was working fine last time I started kubuntu.

---

### Post by johnnytwohats on 2010-02-24
bumping thread. sorry if its against forum rules. I dont know. just desperate for help.

---

### Post by gradinaruvasile on 2010-02-24
Hm. Open alsamixer again and make a screenshot of the window (strech it to the right to all items to be shown) with alt+printscreen. Then attach the picture to a post here (click go advanced , then manage attachments).

---

### Post by johnnytwohats on 2010-02-24
sorry to sound noob, but how do I screenshot?

---

### Post by 23dornot23d on 2010-02-24
ksnapshot is good ..... for screenshots ....

sudo apt-get install ksnapshot

Then go to your menu - graphics - ksnapshot

to find it and run it ......

---

### Post by johnnytwohats on 2010-02-24
here it is

---

### Post by gradinaruvasile on 2010-02-24
Ok... You have several items muted - marked by MM under the volume bars. Navigate to those items with left-right arrows and when on them press m to toggle mute.

And you can lower the Master volume to about 80% just in case.

---

### Post by texaswriter on 2010-02-24
I think it's actually a KDE "bug"... I had the same problem in Sidux... looked up help.. kde sound... and I found the same advice. I think that's just how KDE is... 

Needless to say, yeah, unmute EVERYTHING, lol... :popcorn::KS:D

---

### Post by gradinaruvasile on 2010-02-24
And you may post a picture with the Capture view (press tab in alsamixer to cycle views). To see if the capture devices (such as microphone) are ok.

---

