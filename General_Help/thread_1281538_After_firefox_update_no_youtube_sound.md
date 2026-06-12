---
title: "After firefox update no youtube sound"
date: 2009-10-03
forum: General Help
---

### Post by Cardale on 2009-10-03
I updated last update and after the update I have no sound on all web browser styled videos if its flash or some type of video format or you tube videos.  What could be my issue?

---

### Post by beastrace91 on 2009-10-03
Are you using flash plugin non-free or the open source one? At any rate I'd try reinstalling it via synaptic and see if that helps.

~Jeff

---

### Post by banerjeerupak on 2009-10-15
I'm using ubuntu 9.04. My sound is playing on all my media players. But my web browsers just refuse to play any form of sound. Youtube videos are playing without any sound. And that is not fun at all. I've been using the update manager to keep my system updated each day. 

I've tried using firefox, opera as well swiftfox, which is firefox build specifically for the linux platform. None of them are able to play the sound on youtube videos. 

What should i do to get back the sound on my web browsers? 

:guitar:

---

### Post by juntjoo on 2009-11-28
> **beastrace91 said:**
> Are you using flash plugin non-free or the open source one? At any rate I'd try reinstalling it via synaptic and see if that helps.

~Jeff
 hey, what is synaptic and would you reinstall via synaptic?  i remember having options when installing flash player for firefox and i chose adobe's player, which is giving no sound, but when i uninstalled it and went back to reinstall one of the players that was initially offered, i now can only choose adobe's which im hoping is the problem, but i'd have to be able to get other options, so...  thanks in advance

---

### Post by TheLoneHoot on 2009-12-07
Same here basically.  I upgraded to 9.10 and I have FF 3.5.5.  I do my system updates daily.  Since the upgrade YouTube or other videos in Firefox or Sea Monkey, begin to play w/ sound then go mute.  Then after a few seconds the video will simply freeze.

Rebooting, doesn't help.

I'm pretty much a noob, even though I have had Ubuntu since 7.04... I simply don't know too much about computers.  I've bought and read the pocket guide to Ubuntu (by Kier Thomas) and found it quite helpful, but I don't really get all the "...create a new folder and paste [insert code here]..." stuff.

Are there any plain English instructions on how to fix a simple sound issue?

(I really like Ubuntu but I have to agree with a co-worker:  it's really more of a hobbyist's OS.  I'm forever having to tweak things to make them work.)

________________________________________

Edit:  as a follow-up, I went into the Software Center and uninstalled the flash plugin and then re-installed it, restarted FF, but no fix.

---

### Post by l-x-l on 2009-12-07
I got the following updates in Karmic today & afterwards sound hasn't been right. I can't play sound from 2 sources at the same time. For instance, if I open up a mp3 on VLC and play it, I can't listen to any streaming video in Firefox unless I close firefox & restart. Same problem with chromium, Rhythmbox, etc.. The latest updates broke something.

```

[UPGRADE] bind9-host 1:9.6.1.dfsg.P1-3 -> 1:9.6.1.dfsg.P1-3ubuntu0.2
[UPGRADE] chromium-browser 4.0.265.0~svn20091205r33925-0ubuntu1~ucd1~karmic -> 4.0.266.0~svn20091206r33943-0ubuntu1~ucd1~karmic
[UPGRADE] chromium-browser-inspector 4.0.265.0~svn20091205r33925-0ubuntu1~ucd1~karmic -> 4.0.266.0~svn20091206r33943-0ubuntu1~ucd1~karmic
[UPGRADE] chromium-codecs-ffmpeg 0.5+svn20091202r33521-0ubuntu1~ucd1~karmic -> 0.5+svn20091202r33521-0ubuntu1~ucd3~karmic
[UPGRADE] devicekit-disks 007-2ubuntu3 -> 007-2ubuntu4
[UPGRADE] dnsutils 1:9.6.1.dfsg.P1-3 -> 1:9.6.1.dfsg.P1-3ubuntu0.2
[UPGRADE] libbind9-50 1:9.6.1.dfsg.P1-3 -> 1:9.6.1.dfsg.P1-3ubuntu0.2
[UPGRADE] libdns50 1:9.6.1.dfsg.P1-3 -> 1:9.6.1.dfsg.P1-3ubuntu0.2
[UPGRADE] libisc50 1:9.6.1.dfsg.P1-3 -> 1:9.6.1.dfsg.P1-3ubuntu0.2
[UPGRADE] libisccc50 1:9.6.1.dfsg.P1-3 -> 1:9.6.1.dfsg.P1-3ubuntu0.2
[UPGRADE] libisccfg50 1:9.6.1.dfsg.P1-3 -> 1:9.6.1.dfsg.P1-3ubuntu0.2
[UPGRADE] liblwres50 1:9.6.1.dfsg.P1-3 -> 1:9.6.1.dfsg.P1-3ubuntu0.2
[UPGRADE] libpulse-browse0 1:0.9.21-0ubuntu2~~karmic~ubuntuaudiodev1 -> 1:0.9.21-0ubuntu2~~karmic~ubuntuaudiodev2
[UPGRADE] libpulse-mainloop-glib0 1:0.9.21-0ubuntu2~~karmic~ubuntuaudiodev1 -> 1:0.9.21-0ubuntu2~~karmic~ubuntuaudiodev2
[UPGRADE] libpulse0 1:0.9.21-0ubuntu2~~karmic~ubuntuaudiodev1 -> 1:0.9.21-0ubuntu2~~karmic~ubuntuaudiodev2
[UPGRADE] pulseaudio 1:0.9.21-0ubuntu2~~karmic~ubuntuaudiodev1 -> 1:0.9.21-0ubuntu2~~karmic~ubuntuaudiodev2
[UPGRADE] pulseaudio-esound-compat 1:0.9.21-0ubuntu2~~karmic~ubuntuaudiodev1 -> 1:0.9.21-0ubuntu2~~karmic~ubuntuaudiodev2
[UPGRADE] pulseaudio-module-bluetooth 1:0.9.21-0ubuntu2~~karmic~ubuntuaudiodev1 -> 1:0.9.21-0ubuntu2~~karmic~ubuntuaudiodev2
[UPGRADE] pulseaudio-module-gconf 1:0.9.21-0ubuntu2~~karmic~ubuntuaudiodev1 -> 1:0.9.21-0ubuntu2~~karmic~ubuntuaudiodev2
[UPGRADE] pulseaudio-module-x11 1:0.9.21-0ubuntu2~~karmic~ubuntuaudiodev1 -> 1:0.9.21-0ubuntu2~~karmic~ubuntuaudiodev2
[UPGRADE] pulseaudio-utils 1:0.9.21-0ubuntu2~~karmic~ubuntuaudiodev1 -> 1:0.9.21-0ubuntu2~~karmic~ubuntuaudiodev2

```

---

### Post by TheLoneHoot on 2009-12-07
> **l-x-l said:**
>  The latest updates broke something.

Agreed.

I have no clue what all that code means, but I can tell from the number of folks posting about this issue that there's definitely something funky going on with Karmic.  :(

---

### Post by wqd3tried on 2009-12-08
I am using Firefox in 8.04.3 LTS and also got this problem recently. Sound has also failed on BBC "listen again" and "listen live" audio streaming. I am pretty sure there was no problem when I last used Youtube 2 or 3 weeks ago, and BBC iplayer within the last ten days or less.
All mutimedia files play in Movie Player.

It may be coincidence, but the PC's battery needed replacing and I was manually resetting the clock after powering up for about the same length of time.

(A bigger problem now is that I tried uninstalling and reinstalling Firefox but Synaptic will not reinstall; I'm looking at other threads on this problem but thought the above report might be helpful.)

---

### Post by wqd3tried on 2009-12-08
That middle paragraph is awful.
What I mean is: date and time were first being lost about 3 weeks ago. No other problem noticed until last weekend.

Also, I am writing this on my other PC, running Xubuntu, and the same command: 
cat /etc/issue
gives the same output:
Ubuntu 8.04.3 LTS \n \l
but on this machine the same sound sources are working!
Both machines are *old*.

---

