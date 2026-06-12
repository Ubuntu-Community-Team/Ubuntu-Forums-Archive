---
title: "TonePort UX2 drivers available, but how do I record"
date: 2010-10-16
forum: General Help
---

### Post by MockY on 2010-10-16
I was delighted to see that my TonePort is supported in Ubuntu. I just plugged it in and it was detected. However, how to I use it in Ubuntu? In Windows, I have to start a software called Gearbox in order to start recording with it using Adobe Audition or any other recording software.

I was planning on using Jakosher for Ubuntu, but what do I use in order to initialise the Toneport so that I can start recording with it?

---

### Post by epicnic on 2010-11-14
I'm having the same problem with toneport ux1. It's recognized in "sound" under preferences but I can't hear anything when I select the toneport as an output device.

Worser is that when i select the toneport as input device and try to record something nothing happens. No input what-so-ever.

The only thing working is the green light on the toneport but that's about it.

I'm gonna try and install pod farm and line 6 monkey through wine but from what I already read that doesn't work to good either. Maybe with the 10.10 install it will. I'll let you know.

If there is someone who knows a definite answer to this please post it because I need to record these ideas in my head soon before they just float away.

---

### Post by epicnic on 2010-11-14
So I installed all the OSS pachages available (Read some people had succes with that)
I followed the steps detailed in the following post: 
[http://ubuntuforums.org/showthread.php?t=1163608&highlight=guitarport](http://ubuntuforums.org/showthread.php?t=1163608&highlight=guitarport)

After that I got sound out of the toneport when I tested it with preferences-sound

Installed Wine

Installed line 6 monkey which installs the drivers with Wine

Installed Pod farm with Wine

When I look into the preferences in Wine - Sound I see the toneport under ALSA and when I test the sound I hear it trough the toneport.

When I tried to start the pod Farm I get the message that the device is nog connected which it clearly is off course. Then when I ask to continue anyway I get a windows based error and the program shuts down. It's still loading although which prevents it from having another go at it so I had to kill the process in terminal.

I read that some people had succes with it but nobody is really specific as in how they achieved it (I vaguely heard something about OSS that way but that was basicly all i read about it). I'm pretty much noobish at those things so a step by step explanation would be great.

---

### Post by aza484 on 2011-10-22
Has anyone solved this? I'm having the same issue and its very frustrating as I can use my UX2 for output but not to record!! :(

---

