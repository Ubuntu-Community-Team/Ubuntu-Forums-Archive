---
title: "Skype not ringing through speakers ..."
date: 2010-04-17
forum: General Help
---

### Post by Bucky Ball on 2010-04-17
Any ideas? I fixed Skype to use the Microsoft Lifechat mic/headphones by stopping pulseaudio. All good now but none of the options in Skypes's Options->Sound Devices will get the phone to ring through the speakers. That has been an easy set up on our other machines.

8.04 LTS and Skype 2.1.0.47. Whole reason for this is send SMS in this version of Skype but not previous ... BUT, this version insists on using Pulseaudio and gives no other options in Sound Devices (dumb design idea) and I and a lot of other folk couldn't get Skype happening with Pulse ...

So, all ideas appreciated ... ;)

---

### Post by dzwestwindsor on 2010-07-02
did you fix the prob? I'm not getting a ring either

---

### Post by Bucky Ball on 2010-07-03
Check this thread, specifically post #8:

[http://ubuntuforums.org/showthread.php?t=1478754](http://ubuntuforums.org/showthread.php?t=1478754)

---

### Post by tibike on 2010-07-06
Here is what I did...
I installed PulseAudio Volume Control from Ubuntu Software Center. In PAVC, in the playback tab I set System Sounds to some value (it was set to 0). 
I hope that helps.

---

### Post by psychlic on 2010-07-31
> **tibike said:**
> Here is what I did...
I installed PulseAudio Volume Control from Ubuntu Software Center. In PAVC, in the playback tab I set System Sounds to some value (it was set to 0). 
I hope that helps.
Thanks tibike - same problem here, tried your fix and I can hear Skype ringing again :D

---

### Post by Bucky Ball on 2010-07-31
No such luck for me. I can hear and talk during a call on the headset but can't get the phone to ring through the laptop speakers, only headset. When I get Skype ringing, set playback stream to speakers, ALL output goes to speakers, not headset. I have headset talk/speakers ring setup no problem with Alsa on another box and see no way of doing the same with Pulse. I see this as a major oversight and issue. Therefore I will be going back to Alsa on the laptop so I can turn the regular desktop box which we use for phone now into a server.

Good luck to all. ;)

---

