---
title: "Microphone record does not work cant find fix? Help!"
date: 2010-12-31
forum: General Help
---

### Post by Bushcraft Bill on 2010-12-31
I have a Toshiba Satellite A100 I am using 10.10 I am using headphone/microphone headset this did work for me with 10.04 never a problem, I have tried to use these to fix problem - audacity/sound recorder/pulse audio volume control/pulse audio device chooser/ I am still at a loss to try and figure out how to fix this problem of the mike not working Can anyone try and help me fix this problem please I know its a problem that many have and a fix would help many out....

(the more I use 10.10 the more I love it its been a learning curve I am sure this is just another one of them for me..) 

Bill

Mic Fix as Follows:

Mic fix

Re: Microphone not working after upgrade to Ubuntu 10.10 Maverick
My hardware profile is Duplex. When I click on the input tab the signal measuring bar is always staying lit on the first section and does not move further. This means that the mic is not capturing sound. In 10.04.1 there was a dropdown menu in the input tab from which I could choose the default microphone and thus choose an option that works. In 10.10 there is no such thing. I kind of fixed it by adding "options snd-hda-intel model=3stack" in alsa-base.conf. Now I have the dropdown menu and my microphone works for now. The problem is that I did not have to do this in 10.04.1 ...


options snd-hda-intel model=3stack

sudo gedit /etc/modprobe.d/alsa-base.conf

for mine it was mic 1 and it worked

---

### Post by vangop on 2010-12-31
Did you check in the system->preferences->sound->input tab if the right mic is selected and if it is unmuted.

---

### Post by Bushcraft Bill on 2010-12-31
I did this and nothing -  arecord -vv -fdat foo.wav

yes pic attached

> **vangop said:**
> Did you check in the system->preferences->sound->input tab if the right mic is selected and if it is unmuted.

---

### Post by vangop on 2010-12-31
The bar on input level means the mic is working.
What is on your system->preferences->multimedia systems selector?
Try to play with the settings there.
Did you try to increase the level of input in padevchooser's manager?
Try [this]("http://ubuntuforums.org/showpost.php?p=9696758&postcount=8")

---

### Post by Bushcraft Bill on 2010-12-31
OK pic for multimedia systems selector did play with it nothing worked...


I did up it to 150% and nothing or was that 500 % 


> **vangop said:**
> The bar on input level means the mic is working.
What is on your system->preferences->multimedia systems selector?
Try to play with the settings there.
Did you try to increase the level of input in padevchooser's manager?
Try [this]("http://ubuntuforums.org/showpost.php?p=9696758&postcount=8")

---

### Post by vangop on 2010-12-31
Hi,
your pic of MMS is what I had by default and I also had issues. Is working with these settings:
[IMG]http://i14.fastpic.ru/big/2010/1231/da/3e1c33e6d9bd5faec0d33949e96229da.png[/IMG]
Also, try testing the recording with several apps (soundrecorder, audacity etc) to eliminate the possible issues of a particular app.
If the mic is working, you'll see the input level bar moving in the sound applet.

---

### Post by Bushcraft Bill on 2010-12-31
played with it now for a while nothing no input from mike or no throughput from mike what ever you want to call it... any other ideas you think I could try out?

---

### Post by lidex on 2010-12-31
Or pulseaudio input.

First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

---

### Post by Bushcraft Bill on 2010-12-31
Still nothing I attached screen with what I did with your suggestions you can check to see if I set it up right or wrong....

just a question is their any files from 10.04 that can be moved to 10.10 that would get it to work? since it worked with no problems in 10.04.....

Bill

---

### Post by Bushcraft Bill on 2010-12-31
I also checked I do have the right driver for it or so it says..

---

### Post by lidex on 2010-12-31
If it worked previously, it may be a regression and needs to be reported/fixed. Use this to submit the info:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by Bushcraft Bill on 2011-01-02
Still no worky...

I am going to get a USB Mic just to see if I get lucky with that for input....

---

### Post by Bushcraft Bill on 2011-01-03
I ran some comand and got this could this be the problem if so how do I fix or get this file setup...

sh: /usr/bin/asoundconf: not found
You need to make sure asoundconf is active!

---

### Post by lidex on 2011-01-03
asoundconf has been deprecated. You have to compile/find it yourself if you want to use it and you then have the opportunity to bork your install. Don't say I didn't warn you:
[http://ubuntuforums.org/showthread.php?t=1348604](http://ubuntuforums.org/showthread.php?t=1348604)

---

### Post by Bushcraft Bill on 2011-01-03
I will leave it alone then....

---

### Post by Bushcraft Bill on 2011-01-05
Found fix for mic problem:

Mic fix

Re: Microphone not working after upgrade to Ubuntu 10.10 Maverick
My hardware profile is Duplex. When I click on the input tab the signal measuring bar is always staying lit on the first section and does not move further. This means that the mic is not capturing sound. In 10.04.1 there was a dropdown menu in the input tab from which I could choose the default microphone and thus choose an option that works. In 10.10 there is no such thing. I kind of fixed it by adding "options snd-hda-intel model=3stack" in alsa-base.conf. Now I have the dropdown menu and my microphone works for now. The problem is that I did not have to do this in 10.04.1 ...


options snd-hda-intel model=3stack

sudo gedit /etc/modprobe.d/alsa-base.conf

for mine it was mic 1 and it worked

---

