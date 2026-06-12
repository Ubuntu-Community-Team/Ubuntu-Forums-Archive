---
title: "System/Preferences/Sound doesn't work on karmic without pulseaudio"
date: 2009-11-01
forum: General Help
---

### Post by zob on 2009-11-01
The good old entry for sound setting in System/Preferences/Sound doesn't start on my Karmic on which I uninstalled pulseaudio.

I have a special RME HDSP 9632 sound card which, as far as I know, doesn't work with pulseaudio. That's why I have to uninstall it.

However, I suspect pulseaudio to be that well intregrated into gnome in karmic means that removing pulseaudio means removing the possibility to use GUI configuration of sound settings.

Am I right?

---

### Post by Mr_Bumpy on 2009-11-01
That is correct.  After uninstalling Pulseaudio, I opened gconf-editor, browsed to /system/gstreamer/0.10/default, and set the following values:
audiosink: alsasink
audiosrc: alsasrc
chataudiosink: alsasink
musicaudiosink: alsasink

I don't know if that's the best way to do things, but it seems my audio is working in all programs except for the GNOME movie player (which I have replaced with VLC) and Nautilus' audio preview on mouse hover.

I installed xfce4-mixer to control volume (some people prefer gnome-alsamixer), which I have added to my panel for quick launch.

---

### Post by zob on 2009-11-01
Thanks Mr. Bumpy. That's some nice info.

In the meantime I've been struggling to get pulseaudio working. But it's a nightmare with this card. I'm almost there, I just have some stuttering to get rid of.

But I'll probably uninstall again soon. But it seems to become more and more complicated for each ubuntu version to lose pulseaudio - without losing all the features of the desktop.

---

### Post by JC Cheloven on 2009-11-02
Hi, I'm very interested in this thread, as I also have a dps9632 card which never got working in ubuntu. I didn't imagine that was pulseaudio's fault, althoug it was quite logical (it is recognized in 'aplay -l'). I just saw some other recent posts of yours -zob- about this topic, which made some ligth for me. I'm about to try a couple of things:

a) I'm almost resolved to uninstall pulse, and routing all audio through jack when want multi apps sound. Problems can be: 1.- A few apps can't be routed in jack, but anyway. 2.- This may not lead to an easy way of choosing which card I want to use. 

b) I was considering blacklisting the onboard soundcard in the kernel to see if the 9632 is thus recognized by default. This assumes don't being able to use the onboard card.

I'll come back to post my findings. In the meanwhile I'll be watching this post to see if anyone has any thoughts.
(I'm on karmic BTW)

---

### Post by seeker5528 on 2009-11-02
> **zob said:**
> The good old entry for sound setting in System/Preferences/Sound doesn't start on my Karmic on which I uninstalled pulseaudio.

I don't even have this showing on my menu, I'm not using pulseaudio. What configurations are you expecting it to provide? If you right click the menu applet and choose edit menus, and view the properties of the menu entry, what command does it say it's going to run? 

It could be something that is specific to pulseaudio, did you get rid of the pulseaudio package and all the pulseaudio-* packages? If you are using Synaptic you need to go to 'settings --> options --> general' and uncheck the option to treat recommended packages as options, once the pulseaudio-* packages are removed you can go back and check the box again. Every time packages are updated/installed that recommend pulseaudio you will have to turn off the option to treat recommends as dependencies, there will be some small amount of libraries that are depended on by other packages but these should be a non-issue. 

The menu item that shows up for the gstreamer stuff is 'system --> preferences --> multimedia selector', no need to run gconf for that.

Later, Seeker

---

### Post by zob on 2009-11-02
To make pulse load the module for HDSP the only solution I've found so far is to make at change in the file /etc/pulse/default.pa
```
### Automatically load driver modules depending on the hardware available
#.ifexists module-udev-detect.so
#load-module module-udev-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
load-module module-detect
#.endif
```
As you, in this part of the file, I commented out everything exept one line. Until now it's the only way I can make it work. I am told the I would get a better result if I could use udev (load-module module-udev-detect) to detect the card. It just won't work.
I would be happy to hear from anyone who can make HDSP work in pulseaudio in other way.

At least like this it loads. But what terrible stuttering. It's not usable through pulse.

Today I've (actually without uninstalling pulse) installed jack, and jack plugins for VLC, for audacious and right now I'm trying to make gstreamer output to jack as well.
Again if anyone knows how to do this, I would be happy to hear from you.

But today it's looking better every minute.

I have disabled my onboard sound. It's sad to get sound from that when you have a damn good sound card.

---

### Post by zob on 2009-11-02
It's just the gnome-volume-control seeker5528.
But I've reinstalled pulse AND jack. I don't use pulse, It's just there because removing it made everything look crippled.

I'm working on getting all my sound through jack in this very moment.

---

### Post by cocozz on 2009-11-02
Worked for me, thanks !

> **Mr_Bumpy said:**
> That is correct.  After uninstalling Pulseaudio, I opened gconf-editor, browsed to /system/gstreamer/0.10/default, and set the following values:
audiosink: alsasink
audiosrc: alsasrc
chataudiosink: alsasink
musicaudiosink: alsasink

I don't know if that's the best way to do things, but it seems my audio is working in all programs except for the GNOME movie player (which I have replaced with VLC) and Nautilus' audio preview on mouse hover.

I installed xfce4-mixer to control volume (some people prefer gnome-alsamixer), which I have added to my panel for quick launch.

---

### Post by zob on 2009-11-02
Well actually now that I'm using jack my settings in gconf-editor /system/gstreamer/0.10/default are:

audiosink: jackaudiosink
audiosrc: alsasrc
chataudiosink: jackaudiosink
musicaudiosink: jackaudiosink

That's for jack (of install jack first).
I'm still trying to get sound in my browser. But for now I can just use mediaplayer connectivity plugin in firefox, and then open all media in vlc, that's got a jack-plugin. (Which has to be installed to vlc-plugin-jack).

---

### Post by JC Cheloven on 2009-11-06
Well, as promised, here I am with my findings. 
**I couldn't be happier:** I have now my computer music working flawlessly with the 9632. See my steps:

1) I've follow your efforts these days (including your printer issues with karmic, although unrelated to this). I tried myself everything I figured out to configure hdsp9632 under karmic, till my patiente reached its end.

2) Searched that other people does to do professional audio under linux. There is an amazing amount of them! For example, [this one]("http://createdigitalmusic.com/2009/08/04/linux-music-workflow-switching-from-mac-os-x-to-ubuntu-with-kim-cascone/") is a good article to read. I concluded that Pulse Audio is simply a stick in the wheel if you wanna do serious audio. Everyone's advice is to use only alsa, jack, and nothing more.

3) Installed 64studio, version 3 beta3. It's based on Ubuntu hardy 8.04 LTS with a newer kernel (the "stable" version is based on debian etch, too outdated for my taste). There's not Pulse in this distro, of course. Although beta, this version works very well in terms of stability. Only I wasn't able to activate the nvidia video driver because some missing kernel package in synaptic, which is a minor issue for me.

4) After trying a little, I've found this configuration to work (almost sure I can change sample rate etc, didn't tried yet):
[INDENT]-> Right-click the little loudspeaker in the panel. Go to File-change device-hammerfall DSP (seems to do nothing in practice but anyway).
-> In Jack: driver=alsa, Interface=hw1,0, frames/period=256, 44100Hz, periods/buffer=2, everything else = default.
-> If you are recording from an external source (using the "line in" cables of the 9632), the matching inputs are In11 and In12, which are to be raised in the hdsp mixer. Also you have to route these in Jack to your recording app (I used mhWaveEdit to record from a minidisc, for testing).
-> Playback from apps suporting Jack go through out1 & out2, to outputs A1 & A2, and also to outputs AN1 & AN2. Seen again in hdsp mixer.
-> Playback from apps not supporting Jack (ie. streaming from firefox, I think) will go to the onboard soundcard, which isn't a problem for me: I have both card outputs connected to an amplifier, so I only have to select the correct input in it. I heard that fixing this without blaklisting the onboard card is difficult. [/INDENT]

Sound quality is perfect in playback and recording. I've yet to try recording in duplex mode and several other things, but so far so good. Jack reports 11 ms latency (which I can make even better), and is a pleasure to see less than 9% memory and a 5% cpu in all the above. 

Although it actually doesn't answer the OP's question, I hope this can be of any help.

---

### Post by zob on 2009-11-08
JC Cheloven, I'm happy to hear that. Yeah those pulse-free distros all work like a charm with this card. I guess installing one of those distros will be the way to go.
Right now I'm having a long talk with some ALSA developers. It seems it's an error in ALSA driver, not pulseaudio. It does work without problems in ALSA itself, but the way it kind of "present itself" to a sound server like pulseaudio, stops it from loading the module the right way.

I'll for sure try that 64studio, if not now, then when the final release is here. I wonder if they are waiting to build the final release on the next ubuntu LTS next spring, and to include final release af ardour 3.

---

### Post by JC Cheloven on 2009-11-08
> **zob said:**
>  Right now I'm having a long talk with some ALSA developers. It seems it's an error in ALSA driver, not pulseaudio. It does work without problems in ALSA itself, but the way it kind of "present itself" to a sound server like pulseaudio, stops it from loading the module the right way.  Oh, that's amazing. Look at me, out of ignorance I was blaming Pulse. Also having a second sight at my "way-of-solving", I'm not very proud. I overcame the problem instead of keeping on it like you. My setup worked, sure, but that din't help the community in any way. Your in-deepth approach did. Congrats for being such a smart person.

> I'll for sure try that 64studio, if not now, then when the final release is here. I wonder if they are waiting to build the final release on the next ubuntu LTS next spring, and to include final release af ardour 3.
I haven't seen precise info about this point, but as for my readings, I'd say  that most people doing linux audio stick to LST versions of ubuntu (if using ubuntu). Also I've got the impression that 64studio devs somehow take his time to do things, and they call beta to something almost perfectly stable (much as in the debian's style). So I don't think they will change the base system in the last moment. I'd expect the current 'beta' to be named 'stable' soon, and based in Ubuntu8.04 as it is now.

---

### Post by zob on 2009-11-08
> **JC Cheloven said:**
>  Congrats for being such a smart person.

Je Je (Como dicen en España). I'd wish that someone smarter did this though. I don't understand a word of what they are telling me. It's all code and just a few words that I understand. I just hope that when they finish presenting pieces of code to me, they will have fixed the error.
But thanks for the nice words caballero.

And if you want, you could keep me informed (maybe by PM) if you discover something cool related to HDSP and linux. Or if you post a troubleshooting thread you can PM me to.

---

### Post by JC Cheloven on 2009-11-08
> **zob said:**
> Je Je (Como dicen en España). 
(...)
And if you want, you could keep me informed (maybe by PM) if you discover something cool related to HDSP and linux. Or if you post a troubleshooting thread you can PM me to.
Vale, muchas gracias! De momento sólo puedo decirte que tengo un lío tremendo de cables, reales y virtuales (jack) para probar el full duplex.
//
I'll do it, thanks! As for now, all I can tell you is about a terrible mess of cables, both real and virtual ones (jack), to test full duplex.

Keep in touch (je je) :-)
JC
___________

---

