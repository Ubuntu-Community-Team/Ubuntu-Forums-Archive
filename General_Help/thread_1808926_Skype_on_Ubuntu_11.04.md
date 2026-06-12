---
title: "Skype on Ubuntu 11.04"
date: 2011-07-20
forum: General Help
---

### Post by malel on 2011-07-20
Has anyone managed to suceed in getting 'Skype' to work in Ubuntu 11.04. I have been trying all day but no sucess. I am also a bit suspicious of Pulse audio which seems to have taken over.

---

### Post by alphacrucis2 on 2011-07-20
> **malel said:**
> Has anyone managed to suceed in getting 'Skype' to work in Ubuntu 11.04. I have been trying all day but no sucess. I am also a bit suspicious of Pulse audio which seems to have taken over.


Skype works fine on 11.04 for me. Is this a sound problem only with skype?? Pulseaudio has been standard in ubuntu for a couple of years.

---

### Post by malel on 2011-07-21
Well it started off with it being just the 'Mic' not working but now after having a bit of a play around with it nothing works and the only thing you can select on it is Pulse Audio. I would like to have Alsa as a choice because I have had no trouble with that before.

---

### Post by mastablasta on 2011-07-21
if you "played arround with it" then the easiest solution is to remove completelly it and reinstall it.

---

### Post by malel on 2011-07-23
Thanks the advice but till now still no go with skype . I have uninstalled and reinstalled both skype and pulseaudio but there is still no sound being played back . There is plenty of 'hiss' in the speakers when I turn the volume up but no voice. The mic is plugged in. I even tried 'alsa' but that didn't work either .

---

### Post by RudyG on 2011-07-24
Couple of notes.

1. I had to uninstall pulseaudio from my system as it was producing clicking sounds from all audio output.

2. If you do use pulseaudio you have to uncheck the box in Skype that says "Allow Skype to automatically adjust my mixer levels".
This option can be found in Options -> Sound Devices


Rudy

---

### Post by ssreddy555 on 2011-07-24
> **malel said:**
> Thanks the advice but till now still no go with skype . I have uninstalled and reinstalled both skype and pulseaudio but there is still no sound being played back . There is plenty of 'hiss' in the speakers when I turn the volume up but no voice. The mic is plugged in. I even tried 'alsa' but that didn't work either .

For me, audio worked after installing ALSA mixer & some playing with its controls.

What about video? Is it working?

For me, that too gave a lot of trouble. I somehow made it work after going through the posts here but even now, the video is of a very poor quality.

Skype does have lot of issues - both audio & video - in Ubuntu. May be because it is still in beta. Lot of issues need to be sorted out.

---

### Post by xx58 on 2011-07-24
:rolleyes::rolleyes: Go to Skype website and download Linux version. Skype are Beta Version and when coming up upgrade, then old Beta don't want to work probobly.
Then go sound preferences.
Look your headset or forever you have - click input and check your headset and immitetly you can talk and see if they work. Then go output  .......
Good luck ...

---

