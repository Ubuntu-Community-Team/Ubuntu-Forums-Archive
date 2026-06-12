---
title: "help! how do i make my built in mic default again??"
date: 2009-08-08
forum: General Help
---

### Post by charlie090790 on 2009-08-08
hello, i connected an external mic, and now its the default mic, iknow its the defualt mic because when i use skype, the external mic is the only one which works on the default sound in. and the internal works only on HDA intel (hw:intel,0). and plus the only mic that rosetta stone is picking up is the external one. all i need to know is how to make my built in one default again. im sure this is a bug related to the monitor one [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/327009. ]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/327009")
please help :)

---

### Post by Redache on 2009-08-08
You should be able to set it in the Sound Options. There'll be a "Default Recording Device" option, just switch it to your mic.

I'm not in Ubuntu at the minute so I can't check if it's 100% correct, but I'm fairly certain that there's an option.

---

### Post by charlie090790 on 2009-08-08
volume control>options> input device  ? i only got i-mic and E-mic,   is that it?

---

### Post by Redache on 2009-08-08
It's in System -> Preferences -> Sound.

There's a Sound Caption Option, See if you can get it to work from there.

---

### Post by charlie090790 on 2009-08-08
when i change it to e-mic ,put sound input on defualt and make a test call on skype , i actually get feedback but  no actual sound. and when i do the same with i-mic, i dont get any sound at all back. so e-mac most likely is my built in mic. but im not getting any actual sound back.

---

### Post by charlie090790 on 2009-08-08
everything in the sound preferences is set to autodetect except sound capture which is set to HDA alsa  and device is set to HDA intel(alsa mixer) all the test sounds work except the sound capture

---

### Post by charlie090790 on 2009-08-08
useless ubuntu forums..

---

### Post by Redache on 2009-08-08
The Volume could be set too high on the Mic, Try Lowering the Volume in the Mixer and see if the feedback stops.

---

### Post by charlie090790 on 2009-08-08
theres no mic volume control in the mixer, theres only mic boost which is set to like zero.

---

### Post by mauriceone on 2009-11-25
I have a similar problem with my Toshiba nb100 netbook following installation of 9.10.

Seems that the external mike socket is selected as default rather than the internal mike. I don't know how to change that yet and none of the sound utilities provides a switch to make the change.

However, I discovered that the Audio processing application Audacity permits one to switch between the two mike inputs and the selection is retained for all audio applications until one logs out of Ubuntu.

So I can now use the internal mike for skype, aMSN etc.

Of course, such a solution is pretty naff. Would be better if the sound preferences application included such a facility. Additionally it would be handy if a bright Linux mind could provide simple instruction on how to accomplish this using the terminal.

Thank you to anyone who uses his valuable time to consider a solution.

---

### Post by ubuntator on 2009-11-28
I have the same problem.

I can switch to built-in microphone with success by the command line using $alsamixer than TAB key ...

But no way using Gnome GUI.

I opened a bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/489675](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/489675)

We have to wait and hope

---

