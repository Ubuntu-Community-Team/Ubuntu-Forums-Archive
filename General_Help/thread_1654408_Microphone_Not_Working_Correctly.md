---
title: "Microphone Not Working Correctly"
date: 2010-12-28
forum: General Help
---

### Post by chinggisk on 2010-12-28
Hi there,

I just got a new headset ("Creative Fatal1ty Gaming Headset")to use with some games I play but I can't seem to get it working properly.  I've tested it with both Heroes of Newerth and Teamspeak 3 (Linux clients for both of them) and I get the exact same problem in both - it seems to detect the microphone and sound from it, but intermittently.  When I test it, people can hear my voice but it drops in and out about every half second (So "Hello how are you" sounds like "He-- ho- -re yo-").  

On the other hand if I go into the sound recorder everything works fine.  But the fact that it's exactly the same problem in both of those other programs suggests to me that it's a problem with the way I have my input drivers/settings set up in Ubuntu but I have no idea how to troubleshoot that.  Any suggestions?  I can post logs or something but I don't know what to post (I'm still pretty new to Linux).

---

### Post by Bucky Ball on 2010-12-28
Which Ubuntu release?

---

### Post by chinggisk on 2010-12-28
Oh, right.  10.04, the 64-bit one.

---

### Post by Bucky Ball on 2010-12-28
Do you have the pulseaudio icon in your top taskbar? (a mic and cable)

Click that and choose 'Volume Manager' and go to the 'Playback' tab.
Get the game going and the playback stream should be visible. In the 'Input' tab the mic should be visible. Right click on the stream and make sure it is set to the correct device.

---

### Post by chinggisk on 2010-12-28
I don't have that icon, the only sound related icon is the little speaker with the three sound waves coming from it where you set the volume from.  I have a vague feeling that I may have had to disable pulseaudio at some point in the past trying to fix something else (freezing issues maybe?), I could be completely wrong though.  How would I get it back?

---

### Post by chinggisk on 2010-12-28
Okay, so I installed PulseAudio Manager from the Ubuntu Software Center.  There is only one mic and it is already selected in both playback streams that come up.  I tried fiddling around with the "Lock channels together" and "Set as fallback" buttons but nothing seemed to change.

---

### Post by chinggisk on 2010-12-28
I should also note that when I am in the Input Devices tab in PulseAudio, the little bar at the bottom that detects mic input also seems a bit jarry in the way it is picking up sound, the same way the other programs are.

---

