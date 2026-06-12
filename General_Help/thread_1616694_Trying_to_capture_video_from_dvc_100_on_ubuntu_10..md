---
title: "Trying to capture video from dvc 100 on ubuntu 10.10"
date: 2010-11-08
forum: General Help
---

### Post by xYDOx on 2010-11-08
Argh! I can not seem to find a system to capture video through a dvc 100(pinnacle dazzle) on ubuntu 10.10 I am very new to linux and the command line in general, so in depth explanation is required :P.

Just ask what you need to know in order to solve(as I said I'm not used to this at all).

I also could use some direction to the programs I could use to record the video, I would prefer not to use a virtual machine to capture but if i have to I am willing except for windows (I got a virus and it deleted all of my critical files on windows and I would prefer not to buy it again.)

Any help will be greatly appreciated, thank you.

---

### Post by no2498 on 2010-11-08
put this in a google search 

dvc 100 pinnacle dazzle for linux

---

### Post by nothingspecial on 2010-11-08
I have not tested this, but it has worked for other apps (for me)
```

sudo apt-get install pavucontrol
```

Then start your audio capture app
Then in your menu go Applications > Sound and Video > Pulseaudio Volume Control

Click the recording tab and change "Internal Audio Analogue Stereo" to "Monitor of Internal Audio Analogue Stereo"

That does it for ffmpeg and sound-recorder.

---

### Post by nothingspecial on 2010-11-08
Ah - sorry, video......

...... not sound

ffmpeg is your friend :)

---

### Post by no2498 on 2010-11-08
Linux assumes you know exactly what you`re doing
lol so does windblows

---

