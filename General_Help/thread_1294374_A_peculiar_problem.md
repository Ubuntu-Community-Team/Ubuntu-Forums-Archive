---
title: "A peculiar problem"
date: 2009-10-18
forum: General Help
---

### Post by asamay81 on 2009-10-18
A peculiar problem I have noticed in my system.. first see the screenshot of the alsamixer output

[IMG]http://img444.imageshack.us/img444/2024/screenshottanmaytanmay.png[/IMG]

instead of playback it is showing "capture all".

the sound module is snd-hda-intel. i am using alsa latest version. sound card is Realtek ALC880. the sound playback is very less which i could not improve after a lot of trials. 

the problem i have noticed is when i try to control the volume of audio playback through the volume control bar in the pannel, the sound does not change. when i drag the volume control bar, instead of changing the master or pcm volume, it is changing the volume of the microphone.

i am confused about this problem. rather waiting for a suggestion.

thanks
[IMG]http://img444.imageshack.us/i/screenshottanmaytanmay.png[/IMG]

---

### Post by Sam on 2009-10-18
Have you tried to change the device ? Right click on the volume applet, choose Preferences.

---

### Post by asamay81 on 2009-10-18
thanks...changing the device to Realtec ALC880 (OSS Mixer) helped me. now i could change the volume..

but i am not getting any solution for my very low audio playback

---

### Post by P4man on 2009-10-18
> **asamay81 said:**
> 
instead of playback it is showing "capture all".

No you are misreading. Playback is selected. Using tab key you can change to capture and all.

I assume you're jaunty. Pulseaudio is somewhat weird to configure in jaunty. First of all, go to system > preferences > sound. make sure everything is set to pulse audio and the default mixer to pulse playback of your soundcard.

then open a terminal and type 
```

sudo apt-get install pavucontrol
```

(or install pavucontrol through synaptic if you prefer using GUI)

then open pulse audio volume control from apps > sound and video.

See if you can fix it there.

---

