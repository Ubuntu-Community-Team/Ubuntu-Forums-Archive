---
title: "New install of Lucid and no sound:"
date: 2010-04-30
forum: General Help
---

### Post by djxcon on 2010-04-30
New install of Lucid and no sound:

**** List of PLAYBACK Hardware Devices ****
card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The volume is not muted.

---

### Post by xkjq on 2010-05-01
try running
```
alsamixer
```
in a terminal and see if any channels are muted

---

### Post by sosias on 2010-05-01
In my case sound (including sound control applet) disappeared after upgrading my karmic to lucid yesterday. Card ( cm8738 ) is correctly recognized, nothing is muted. I'm clueless.

---

### Post by djxcon on 2010-05-01
What I have found is that the audiophile card works with alsa only through jack and not through pulseaudio.

I have an external USB sound card that does work with pulseaudio.

So that I dont have to always use jack to get my audiophile to work, and not have to use the USB card, do I have any other options?

---

### Post by lidex on 2010-05-01
Alternate channel mappings needed for ICE1712

Cards such as Audiophile 2496, Delta 1010LT and others using the ICE1712 chip, there is a bug with the channel mapping.

Diagnosis

Open a terminal, then enter this command:

cat /proc/asound/cards | grep ICE1712

If you get a line specifying the name of your soundcard, you're probably affected.

Fix / workaround

See [bug #178442]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442").

---

### Post by sbike on 2010-05-02
I have the same problem with the CMI8738.  Although it's not quite no sound.  The login greeting sound works, and various desktop sound effects work.

But even though I have earphones plugged into the sound jack I only hear the rear channels.  So with videos I hear background noises, and with music I hear only the non-vocals.  I guess I'm missing the center channel.  It must think I'm in surround sound mode and I just want normal stereo.

How can I switch it to normal stereo mode instead of surround mode.  I just want earphones to work.  Oh btw:
$ cat /proc/asound/cards 
 0 [CMI8738        ]: CMI8738-MC6 - C-Media CMI8738
                      C-Media CMI8738 (model 55) at 0xe800, irq 20
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfbdbc000 irq 17

So I don't have the ICE1712 as lidex mentioned.

lspci reports:
05:00.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

BTW, this did work in the lucid pre-release, but even if I try the older kernels it's still broken.  I'm guessing something with state (that a reboot or previous kernel doesn't reset) changed.

I tried logging in as a new user (to rule out any per used config) and had the same problem.

I tried also mixer and unmuted everything and put it at max volume, the one strange thing is if I *unmute* the mic, I lose all audio and can't hear what little I could before of music/video playing.

I found the alsa-info script, I thought the resulting info might be helpful:
thought it might be [http://www.alsa-project.org/db/?f=c8abb5dad45cf0065564277fd65c22af6ea988b3](http://www.alsa-project.org/db/?f=c8abb5dad45cf0065564277fd65c22af6ea988b3)

---

### Post by lidex on 2010-05-02
sbike: You should really start a new thread - it gets confusing with multiple and possibly unrelated issues. Having said that, take a look at the attachment. Looks like your default card is the CMI, but dmesg shows it's irq is disabled. Try upgrading to latest alsa following the direction in this post:
[http://ubuntuforums.org/showpost.php?p=9136618&postcount=2]("http://ubuntuforums.org/showpost.php?p=9136618&postcount=2")
Also have a look here:
[http://www.google.com/search?q=CMI8738-MC6&sitesearch=ubuntuforums.org]("http://www.google.com/search?q=CMI8738-MC6&sitesearch=ubuntuforums.org")

---

### Post by mpennell on 2010-05-02
yesterday someone suggested entering:

alsactl init

I'm from the Still Not As High As Absolute Beginner Talk forum so I have no idea what those magic letters mean, and why they work, but it does seem to have worked to bring back sound (except for not having any "sound" section in my preferences).

---

### Post by yosoyeleze on 2010-05-05
Hello:

Please. Help me! I have a Audiophile 2496 soundcard, and pulseaudio on ubuntu 10.04 show only the digital output. I try uninstall pulseaudio.
I used Ubuntu hardy for professional audio production, and this distribution work fine.

solutions?

---

### Post by sbike on 2010-05-06
Will do.  I upgraded to the newest alsa and it didn't help.  I'll start a new thread called "10.04 lucid CM8738 problems."

---

### Post by dino99 on 2010-05-06
install paprefs and gnome-alsamixer (tweak it with your prefs)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by lkrory21 on 2010-05-10
Regarding M-Audio Audiophile 24/96 soundcard (and probably other soundcards with the same chipset although the code below might need a bit of tweaking) and analog sound output with Ubuntu 10.04 you can try the solution described in the link below which involves creating two different files:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63)

It was working in Karmic and as I can verify it is also working this way with Ubuntu 10.04 (Lucid Lynx). 

Cheers!

---

### Post by wavesound on 2010-06-01
HI All
I see this is still a major problem.
I still have no sound from my Audiophile 2496.
Which has worked in all other distro's.

I fail to see why the developers think it OK to have no sound on a modern computer system. Also the fact that this sound card is well supported by Alsa.
Alsa just fails to load and pulse cannot connect to the card.
I hope the press don't get to hear about this or the MS fan boys.

Cheers in silence :confused:

Bob

---

