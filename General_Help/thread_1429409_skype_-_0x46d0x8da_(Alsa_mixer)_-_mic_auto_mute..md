---
title: "skype - 0x46d:0x8da (Alsa mixer) - mic auto mute."
date: 2010-03-14
forum: General Help
---

### Post by Zidaps on 2010-03-14
Hi 

I'm having a problem with my USB mic, its integrated into my webcam. On the system bar at the top of the desktop, I click on the speaker icon to open the Volume Control. Whenever I select the _device_ "*USB Device 0x46d:0x8da (Alsa mixer)*" the mic is always muted (crossed out). Even if I change _device_ to "*HDA NVidia (Alsa mixer)*" - When I change back to the _device_ "*USB Device 0x46d:0x8da (Alsa mixer)*" the mic is back on **mute**. It seems to go back to mute automatically. Is there any way to solve this? (Its not listening to me !!! )

This is primarily so that I can get my mic working with skype 2.1 I'm using Ubuntu 9.04 - I've checked the **Options > Sound Devices**. I cannot select anything else but "PulseAudio server (local)". So for (Microphone, Speakers, and Ringing) the only option available is "PulseAudio server (local)".

I've tried going to **System > Preferences > Sound**. And literally tried every combination of* Device* and *Sound Capture* there is. Still nothing, the "Test" doesn't make any beeping sound for the *Sound Capture*.

Any Ideas?? Thanks.

---

### Post by gare on 2010-03-14
Hello,


I've had similar issues, and found that there are two different paths you can take:

Upgrade your way out of problem.  Ubuntu 9.10 has fewer issues with Pulse Audio and Skype 

Make sure using the latest version of skype:

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

Version 2 recently came out for Ubuntu.

2. 
You can also download an older version of skype that allows you to change the audio source.  These forums for the how to..


good luck.

---

### Post by Zidaps on 2010-03-14
Thank you very much...

I've gotten version 2.1 to work by disabling pulseaudio. Using the link you provided. I simply uninstalled Skype in synaptic. The did the following commands in terminal:

> 
killall pulseaudio
sudo aptitude remove pulseaudio
sudo aptitude install esound
sudo aptitude remove /etc/X11/Xsession.d/70pulseaudio

And that was it... re-installed skype and I could not see other sound devices and select the proper device for the mic etc...

Thanks again.

---

