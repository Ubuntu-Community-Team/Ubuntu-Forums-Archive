---
title: "MuseScore"
date: 2009-11-08
forum: General Help
---

### Post by Atzu on 2009-11-08
Hello,

Hmm... I wasn't really sure where to post this...
Well the thing is that I want to be able to edit/make music scores... Like Finale (Windows) So I found This program called MuseScore which looks like the program I need, I downloaded and installed... (from repos), everything looked fine, but when I opened it and tried to use I had no sound... (It's supposed to have playback) I think it's something to do with midi playback... So if anyone could help me with this :/ Thanks in advance!

---

### Post by Atzu on 2009-11-08
Oh and I forgot to tell I'm using Karmic

---

### Post by JC Cheloven on 2009-11-19
Hi, switching from sibelius here. I can confirm that musescore is a valid aternative. For me at least. 

First of all, I'd recommend to use v0.9.5, it has been way more stable for me than the one in the repos (0.9.4). You can find in launchpad a [ppa from the developers]("https://launchpad.net/~mscore-ubuntu/+archive/ppa"). 

And the sound problems, I think are related, once again, to PulseAudio. The first thing I've tried is to create the file ~/.pulse/client.conf and stuff it with this single line ```
autospawn = no
``` 
Then reboot, and before running musescore type at terminal ```
pulseaudio -k
``` When you're done you can wake pulse again by pulseaudio -D

I had only partial success with this. For example I found problems when playing something in totem and applying the procedure afterwards. I'm looking forward to try that it's said [in this post]("http://ubuntuforums.org/showthread.php?t=1313253"), rather than further investigage my present method.

Greetings

---

### Post by Atzu on 2009-11-19
Thanks! ^.^ I'll try this as soon as I can... If you find out about more solutions please tell me I'll be checking this thread :p anyway I'll try this and thanks a lot!

---

### Post by JC Cheloven on 2009-11-19
> **Atzu said:**
> Thanks! ^.^ I'll try this as soon as I can... If you find out about more solutions please tell me I'll be checking this thread :p anyway I'll try this and thanks a lot!

I just tried in a spare machine the elaborated method of said post. It is not so complicated to apply, and it seems able to fix both serious problems I have with sound. Basically it wipes pulse and tells alsa & gstreamer to do what pulse did. Note that "my method" may be sufficient for most people, but I'm looking for something else that also solves my hardware issue.  Please see my post there, and come back if you have any questions ;-)

Now I'll carry on testing everything before deploying UbuntuStdio in my big machine, to compete with 64studio.

---

