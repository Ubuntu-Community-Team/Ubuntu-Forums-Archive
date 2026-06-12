---
title: "Cannot get a mic working in Skype 2.1.0.47"
date: 2009-09-24
forum: General Help
---

### Post by parubok on 2009-09-24
Updated to Skype 2.1.0.47 and the mic stopped to work :(
I googled the problem, but didn't find a satisfactory solution (some propose to remove PulseAudio - is it that bad?).

My configuration:
OS: Ubuntu 9.04
PulseAudio sound server: 1:0.9.14-0ubuntu20.2
Mic device: Logitech QuickCam® Pro 9000

By the way - video capture works OK.

---

### Post by TheStroj on 2009-09-24
I had the same problem and I think I know how you will fix yours.

You need to install the PulseAudio Device Chooser utility using Synaptic
More info here:
[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

It is really easy. Run skype phone call and then go to PulseAudio Device Chooser Utility and search for skype under "Input" tab. Right click on it and choose the input device.

---

### Post by parubok on 2009-09-24
Thanks TheStroj!
It worked.

In 'Volume Control', tab 'Recording', use 'Switch stream' command to select the right device (during Skype call).
I understand that the change is permanent, e.g. no need to repeat the process each time you restart.

---

### Post by TheStroj on 2009-09-25
No problem ;)

---

### Post by cgroza on 2009-09-25
I had the same problem...Then I started to mess up the audio settings in skype...and i picked the right ones...i was lucky.

---

### Post by Pasdar on 2009-10-11
> **cgroza said:**
> I had the same problem...Then I started to mess up the audio settings in skype...and i picked the right ones...i was lucky.


You have an older version of Skype. There is no "right settings" in the new one... there is just one and that is already selected.

---

### Post by pjalegria on 2009-10-11
I have the same problem on Karmic and i can get it to work

---

### Post by antonkedrov on 2009-10-11
> **pjalegria said:**
> I have the same problem on Karmic and i can get it to work

Hi!
can you try to switch your input source at volume manager applet? i have mic & front mic sources at my acer notebook - may be this is the reason :popcorn:

---

### Post by pjalegria on 2009-10-11
Here there are my settings:

[IMG]http://img230.imageshack.us/img230/5909/capturaecra1.png[/IMG]
[IMG]http://img200.imageshack.us/img200/5720/capturaecra2p.png[/IMG]

---

### Post by antonkedrov on 2009-10-11
sorry, pjalegria, seems karmic have other sound applet. i'm waiting for release 9.10, so i can not help you right now.
i can only advise you to turn off "automatic sound configuration" at skype settings and turn on your microphone playback at gnome sound settings so you can hear your voice in realtime when you talk to microphone.
i hope you fix your problem with microphone soon.

---

### Post by pjalegria on 2009-10-11
ok thanks

---

### Post by diehardlinux on 2009-10-23
With your posts, and a email from skype support, I was able to get skype 2.1.0.47 64bit for ubuntu 9.04 (kernel 2.6.28-15-generic) working with my logitech e3560 webcam with mic.

Here are the steps I took to get it working:
1) Installed application: padevchooser (synaptic or apt-get) ,restart the system.
2) change sound devices (under system preferences sound): change sound capture to OSS recording device VS. Alsa recording device.
3) Start padevchooser (applications, sound/video,pulseaudio device chooser) "click the jack icon near the clock top right and select configure local sound server and click the tab most to the right called simultaneous output and tick the option add virtual output device for simultaneous output" ([http://forum.skype.com/index.php?showtopic=178321](http://forum.skype.com/index.php?showtopic=178321)),
4) start skype.

recording should now be working for skype.

To test recording for both skype and the system I checked pulse audio volume recording, and sound recorder (application, sound/video).

Then I placed a test call with skype. I also ran my rhythmbox media player for sound to check if I was able to simultaneously listen to and record audio.

Hope that helps everyone else out.

:popcorn:

---

