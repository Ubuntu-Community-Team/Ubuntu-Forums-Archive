---
title: "Record Audio From Speakers"
date: 2010-05-09
forum: General Help
---

### Post by physic.dude on 2010-05-09
I need to record the audio that passes through my speakers in stereo and good quality. I'm not sure what settings are needed but any help would be great.

---

### Post by unplugged23 on 2010-05-09
I'm pretty sure you can do that with audacity, although I couldn't tell you how. I've just hear of others doing it.

---

### Post by Bucky Ball on 2010-05-09
A good microphone is pretty essential, preferably stereo if that is what you are after.

What quality are you looking for, eg CD quality, or better? And does it need to be any particular file type or size?

---

### Post by itsjareds on 2010-05-09
Audacity can do this by recording sound directly from your sound card.

First, install audacity:

```
sudo apt-get install audacity
```

Getting the audio to actually record was a bit tricky for me -- I just messed with the settings until it worked. I do want to note that it does record for me only after I change a setting in the volume control. Click on the volume applet and choose Sound Preferences, then choose the Hardware tab. I had to change Profile to "Analog Surround 5.0 Output", then recording worked perfectly.

---

### Post by physic.dude on 2010-05-09
I have audacity but I have no idea what the settings in audacity should be, same with the sound preferences. Can you tell me yours?

And I will not use a microphone.

---

### Post by itsjareds on 2010-05-10
For Audacity's settings, I believe all of mine are default. In Edit > Preferences > Devices, I have ALSA as my host and "default" device on 2 channels (stereo).

In the sound manager (click sound indicator icon and click Sound Preferences), choose the Hardware tab and, you might have to tweak this until it works, but choosing the profile "Analog Surround 5.0 Output" made it possible for me to record. If that does not work then try other profiles until you get one that will record.

---

### Post by physic.dude on 2010-05-10
Wait,
I cant record audio from other programs like Freebirth!!!
One or the other will lock up.

---

### Post by ell02 on 2010-05-10
The PulseAudio Controls
If you want to be able to record what is playing in your speakers or have your music play on all your devices at the same time you need the Pulse Audio Controls. You can get these from the Ubuntu Software Center/Sound and Video. If you select the Pulse Audio Device Chooser it will install the rest automatically and they will appear in Applications/Sound and Video. Click on the Pulse Audio Device Chooser. This will put a little audio jack icon on your panel. Left click on it and choose preferences and check the box Start Applet on session login if you want it to stay there when you reboot.

Recording what is playing in the Speakers
Now that you have the Pulse Audio Controls this is easy. Open the Pulse Audio Volume Control from pa device chooser. Click the Input Devices tab. At the bottom click the box nest to Show: and select All Input Devices. Now, along with all the hardware input devices there are Monitors for them that will give you access to their outputs. To set the default device to one of the Monitors click on the green icon. To test this open Sound recorder and, with something playing through the device you selected the monitor for click record and record a few seconds. Now play it back. Viola!!


[http://ubuntuforums.org/showthread.php?p=8043003](http://ubuntuforums.org/showthread.php?p=8043003)

---

### Post by mjitkop on 2010-05-23
> **ell02 said:**
> The PulseAudio Controls
If you want to be able to record what is playing in your speakers or have your music play on all your devices at the same time you need the Pulse Audio Controls. You can get these from the Ubuntu Software Center/Sound and Video. If you select the Pulse Audio Device Chooser it will install the rest automatically and they will appear in Applications/Sound and Video. Click on the Pulse Audio Device Chooser. This will put a little audio jack icon on your panel. Left click on it and choose preferences and check the box Start Applet on session login if you want it to stay there when you reboot.

Recording what is playing in the Speakers
Now that you have the Pulse Audio Controls this is easy. Open the Pulse Audio Volume Control from pa device chooser. Click the Input Devices tab. At the bottom click the box nest to Show: and select All Input Devices. Now, along with all the hardware input devices there are Monitors for them that will give you access to their outputs. To set the default device to one of the Monitors click on the green icon. To test this open Sound recorder and, with something playing through the device you selected the monitor for click record and record a few seconds. Now play it back. Viola!!


[http://ubuntuforums.org/showthread.php?p=8043003](http://ubuntuforums.org/showthread.php?p=8043003)

Thank you for these instructions with PulseAudio. I am using Ubuntu 10.04 and these instructions worked exactly as you decribed. I am now able to simply use the pre-installed Sound Recorder application to record streaming radio. :guitar:

---

### Post by hartguy on 2010-08-26
I know it's been a few months, but thanks itsjareds! I set mine on "Analog Surround 4.0 Output" for hardware (I found it strange that there were no devices under "Sound Input"), kept Audacity settings as the default, and it records from the speakers perfectly! I'm running Lucid Lynx on an Inspiron 1525. Thanks again! :D

---

### Post by inameiname on 2010-08-26
I found this a while back:


[http://www.omgubuntu.co.uk/2010/07/quickly-record-soundcard-output-in.html](http://www.omgubuntu.co.uk/2010/07/quickly-record-soundcard-output-in.html)

---

### Post by PGScooter on 2010-08-30
> **inameiname said:**
> I found this a while back:


[http://www.omgubuntu.co.uk/2010/07/quickly-record-soundcard-output-in.html](http://www.omgubuntu.co.uk/2010/07/quickly-record-soundcard-output-in.html)


thank you inameiname,
out rec is super simple to install and use. The gui is not very attractive, but I don't mind because it works great.

---

### Post by inameiname on 2010-08-30
No problem. Glad it worked for ya.

---

