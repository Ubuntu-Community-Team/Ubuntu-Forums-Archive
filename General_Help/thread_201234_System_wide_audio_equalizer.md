---
title: "System wide audio equalizer?"
date: 2006-06-21
forum: General Help
---

### Post by Shay Stephens on 2006-06-21
I have done some searching and found that xmms has an equalizer, but what about a system wide equalizer?  I use rhythmbox for listening to music and mplayer for listening to radio streams, but the sound coming from ubuntu has too much bass.  

Is there anything I can do?

---

### Post by grendelkhan on 2006-06-21
It would have to be an addon for either esd or alsa and I don't know of anything that would do this.

---

### Post by gookie on 2006-06-22
I'm also interested in this. Most, if not all, of the music player which are library based are lacking equalizer or audio enhancers. While the simple audio players (xmms, bmp, etc) have amazing equalizer support, but you cant organize your music within them.

---

### Post by dilidon on 2006-06-28
Same. Is there a global tool to do it, so it would cover anything, including totem, rhythmbox (which I've replaced with Amarok, solely because it does not have an equalizer), etc.

---

### Post by mcduck on 2006-06-29
only thing I can think of would be installing Jack and then using it to route all audio throuh some EQ plugin.. But I'm not sure how many apps actually have a jack output plugin available..

---

### Post by Shay Stephens on 2006-08-30
Well it's been two months and I still have not found anything that would let me change the amount of bass that comes out of the speakers.

If anyone has any ideas I am open to them.  I think I might even look to see if there is a harware solution I could piece together.

---

### Post by xtknight on 2006-08-30
Some of the alsa drivers have bass/treble adjustment options in the mixer.  Mine don't actually do anything though.

---

### Post by kovan on 2006-09-17
Ping.
Same here.

---

### Post by vlghltlh on 2006-09-29
I am also wondering about this.

---

### Post by EDevil on 2006-11-21
Me too.

---

### Post by marx2k on 2006-12-01
I've been looking for an answer to this issue as well.

I thoroughly enjoy using RhythmBox audio player, however it does lack the one thing I need to make these desktop stereo speakers sound better: an equalizer.

A systemwide equalizer would be really nice!

Anyone? Anyone?

---

### Post by ridetheteapot on 2006-12-01
alsa equalizer would be the sweetest thing in the word ever. i'd like it for tweaking line-in sound.

---

### Post by kenox on 2006-12-03
Use jamin with jack. Xmms has jack plugin.

---

### Post by Shay Stephens on 2006-12-03
> **kenox said:**
> Use jamin with jack. Xmms has jack plugin.

But that is only xmms right?  It wouldn't work with something like mplayer would it?

---

### Post by Shay Stephens on 2006-12-03
I found the jack website, and they provide a list of applications that can use jack:
[http://jackaudio.org/applications](http://jackaudio.org/applications)

mplayer is on the list.  So I will do some looking around to see what I can find :D

---

### Post by Yuzem on 2006-12-06
I'm not sure but this seems an equalizer plugin for gstreamer or something like that:
[http://rpmfind.net/linux/RPM/conectiva/snapshot/i386/RPMS.extra/gst-plugins-equalizer-0.8.7-74961cl.i386.html](http://rpmfind.net/linux/RPM/conectiva/snapshot/i386/RPMS.extra/gst-plugins-equalizer-0.8.7-74961cl.i386.html)

---

### Post by rhclaus on 2007-02-17
Maybe try this? 

[http://sourceforge.net/projects/rteq/](http://sourceforge.net/projects/rteq/)

---

### Post by todayalemon on 2007-02-28
this project seems to be dead for years. but does anybody know of something else? The idea is quite interesting.

---

### Post by hotani on 2007-03-09
This would be a very good thing. For a while I used Amarok for music just because it had an EQ. Since I can't stand the layout, I went back to rhythmbox. Solution to the bass problem? I stuffed a towel in the subwoofer blow-hole. It makes a fairly decent EQ! :) 

To add more bass with towel EQ: don't stuff it in so tight
To reduce bass with towel EQ: wad up so it fits blowhole tightly

It works system-wide!

---

### Post by Toins on 2007-03-12
Hi guys,

I have the same problem and it will be resolved soon...
It seems that there's an equalizer in the last version of gstreamer and there's already a patch for exaile:
[http://www.exaile.org/trac/ticket/1](http://www.exaile.org/trac/ticket/1) 

Cheers

---

### Post by gosh on 2007-03-13
> **Toins said:**
> Hi guys,

I have the same problem and it will be resolved soon...
It seems that there's an equalizer in the last version of gstreamer and there's already a patch for exaile:
[http://www.exaile.org/trac/ticket/1](http://www.exaile.org/trac/ticket/1) 

Cheers

Does anyone know how to install the gstreamer-equalizer?
In which module can I find it?

---

### Post by gosh on 2007-03-13
> **gosh said:**
> Does anyone know how to install the gstreamer-equalizer?
In which module can I find it?

It should be in the gst-plugin-bad module.
I compiled the csv version of gstreamer and the gst-plugin-bad module, but exaile (svn-version) still says 

```
Gstreamer equalizer is not available. It can be found in gstreamer-plugins-bad (currently found in GTS CSV).
```

---

### Post by ceedubu on 2007-08-01
Not sure if this will work for your sound card, works for mine (audigy 2).

Anyway, I just use the ALSA mixer Bass and Treble controls. The thing is that you have to make sure that 'Tone' is also selected, otherwise it has no effect... or is it affect...

Alsa Mixer -->
Edit -->
Preferences --> check 'Tone', 'Bass' and 'Treble' --> close
Back to Alsa Mixer....
Switches Tab --> Check 'Tone' -->
Playback tab --> now your bass and treble sliders should work.

hope this helps.
c

---

### Post by Shay Stephens on 2007-08-01
> **ceedubu said:**
> Not sure if this will work for your sound card, works for mine (audigy 2).

Anyway, I just use the ALSA mixer Bass and Treble controls. The thing is that you have to make sure that 'Tone' is also selected, otherwise it has no effect... or is it affect...

Alsa Mixer -->
Edit -->
Preferences --> check 'Tone', 'Bass' and 'Treble' --> close
Back to Alsa Mixer....
Switches Tab --> Check 'Tone' -->
Playback tab --> now your bass and treble sliders should work.

hope this helps.
c

Are you talking about the terminal program "alsamixer"?  How do you get to the edit function?

---

### Post by offchance on 2007-11-26
me three. if I can make fire and cubes show up on the screen with my nvidia graphics card then I ought be able to do something as simple as turn down the bass a little with the nvidia/conexant sound hw.

---

### Post by FuturePilot on 2007-11-26
It's on the way :) Will most likely be in Hardy
[http://www.pulseaudio.org/]("http://www.pulseaudio.org/")
[https://blueprints.launchpad.net/ubuntu/+spec/cleanup-audio-jumble]("https://blueprints.launchpad.net/ubuntu/+spec/cleanup-audio-jumble")
PulseAudio is a very advanced sound server

---

### Post by tremby on 2008-01-05
i have a fairly old soundblaster live.

took me a while to figure this out, and i'm a tad late but here is my solution:

alsamixer from the command line and set up everything how i like it -- rear speakers louder than the front ones, mic set up as recording device etc.

press m with "tone" highlighted to switch on eq (this is what i hadn't figured out) and adjust bass and treble as necessary.

quit alsamixer and run
alsactl -f ~/.alsactl.state.eq store

run alsamixer again, switch the eq back off, exit. then
alsactl -f ~/.alsactl.state store

now i have sound profiles saved with and without eq switched on. i have the normal one restored at kde startup and then i restore the one with eq to cut the bass at night so as not to piss off my housemate below! the restore commands:

alsactl -f ~/.alsactl.state restore

alsactl -f ~/.alsactl.state.eq restore

i've made a little shell script for each of these commands so i don't have to remember them.

---

### Post by Shay Stephens on 2008-01-05
> **tremby said:**
> i have a fairly old soundblaster live.

press m with "tone" highlighted to switch on eq (this is what i hadn't figured out) and adjust bass and treble as necessary.


I checked in alsamixer and I don't see a "tone" entry that can be highlighted.  Might be hardware specific to the sound blaster?

---

### Post by tonychar on 2008-01-06
Yep, me too.  My Logitech speakers are great, but way too bassy.

---

### Post by Dominicano731 on 2008-07-12
Here's a solution I found while desperately looking around to reduce my bass.  I got these instructions from [here]("http://ubuntuforums.org/showthread.php?t=476146") where someone was trying to fix a sound problem on their laptop.

Type this into the terminal to install C* Audio Plugin Suite
```
$ sudo apt-get install caps
```

Create a new asoundrc file
```
gedit ~/.asoundrc
```

Insert the following text into the new file:
```
   pcm.!default {
       type plug
       slave.pcm "equalized";
   }

   pcm.equalized {
       type ladspa
       slave.pcm "plug:dmix";
       path "/usr/lib/ladspa";
       plugins [
           {
               id 1773
               input {
                   controls [ -8 -4 -1 0 0 0 0 0 0 0 ]
               }
           }
       ]
   }

```
The numbers in the controls array are the equalizer presets :)
I don't know the range, but I've tested it, and it reduces my bass very well.  You need to restart the program using alsa for it to take effect though.
Make sure you keep a backup of your old asoundrc file if it existed.

---

