---
title: "Karmic 9.10 Sound Meltdown - Horrific!"
date: 2009-11-16
forum: General Help
---

### Post by kschanaman on 2009-11-16
I just migrated from using PCLOS to Ubuntu Studio 6.10 64-bit Edition since I've gotten serious about sound and video editing. To my dismay, Karmic hasn't been a very welcoming soul in the sound department. I realize those who are into video and sound editing may scoff at me for using on-board sound and video, and I agree this isn't the most realistic way of getting started, but this machine is capable. It's the sound that is messing things up, and (puke) Windows 7 has no issues on my system whatsoever. The problem is Karmic. 

**The System**

Operating System: Ubuntu Studio 6.10 64-bit
eMachines ET1331G-03W 64-Bit
Processor: AMD Athlon II X2 2.7 GHz
Ram: 6 GB
Audio: nVidia HD / Realtek 1200, Integrated
Video: nVidia GeForce 6150SE / nForce 430, Integrated
PCI Add-On Devices (1):  Belkin IEEE 1394 Firewire card, 3-port

**The Problem**

1. When trying to start Xine and Totem, video freezes when audio begins to play. Audio intermittent, stutters; both Xine and Totem lock up. 

2. When recording in Audacity, no microphone connected to system and Microphone mixer control muted or on (makes no difference), recording level meter shows -24 decibels (halfway across level meter). Source of this noise is coming from sound system. 

3. Ubuntu login sounds distorted with a "tinny" sound and is just plain awful. 

4. Audio becomes distorted and "tinny" regardless as to which mixer elements are muted or adjusted, even if setting all levels down to 75 percent

5. Audio in Audacity shows recording audio of right stereo track above the center dB line.

6. Audio begins to stutter when using Xine or Totem's "Jump to Chapter" button and never recovers. When allowed to play straight through from beginning to end with no interference, audio stops halfway through movie. 

7. Hydrogen drum sequencer has a tinny, distorted "echo" when using the "Kick Drum", but sounds normal when switching its audio interface setting to OSS rather than ALSA (which indicates my system-wide problem may be ALSA instead of Pulseaudio(?))

**What's Been Done Already**

* Made changes to /etc/pulse/daemon.conf to the following, per another thread I located wherein this fixed the problem for some, but not for me: 

; resample-method = speex-float-1
resample-method = ffmpeg
; enable-remixing = yes
enable-lfe-remixing = true

* Made changes to /etc/modprobe.d/alsa-base.conf at the end of the file, commending out 'options snd-hda-intel power_save=10 power_save_controller=N' which did fix the loud popping sound every several seconds. Also changed snd-hda-intel model to '6stack-dig' which has helped others with the driver detection for the integrated sound, according to other forums, but still no joy for me.  The end of my alsa-base.conf now appears as follows, with no additional detriment OR improvement:

# Power down HDA controllers after 10 idle seconds
#options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel model=6stack-dig
#options snd-hda-intel model=auto probe_mask=1

**Summary**

I would really like to stay with Studio 64-bit Karmic, as it appears it has everything I need. Even got Cinelerra installed, but having audio issues with it as well. It doesn't seem to like Pulseaudio at all. 

Any ideas or suggestions would be greatly appreciated. Thank you!

Kurt

---

### Post by kschanaman on 2009-11-16
I forgot to add the results of: lshw -class sound 

This provided me with the following information regarding the sound on this board: 

*-multimedia
description: Audio device
product: MCP61 High Definition Audio
vendor: nVidia Corporation
physical id: 5
bus info: pci@0000:00:05.0
version: a2
width: 32 bits
clock: 66 MHz
capabilities: pm msi ht bus_master cap_list
configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
resources: irq:21 memory: dfe78000-dfe7bfff

Hopefully this might be of help also.

---

### Post by arnab_das on 2009-11-16
see if this works.

[http://thoughtsndreams.wordpress.com/2009/11/14/install-restricted-extras-for-ubuntu/](http://thoughtsndreams.wordpress.com/2009/11/14/install-restricted-extras-for-ubuntu/)

---

### Post by kschanaman on 2009-11-16
Guess I must not have clearly stated the problem. The issue isn't with the codecs, as they are already installed. Already have ubuntu-restricted-extras installed. The sound problem is system wide, affecting all applications that use sound. Not a good thing considering the name: Ubuntu "Studio"  A studio cannot use Ubuntu "Studio" when the sound has such serious issues. 

This is either an ALSA problem or a Pulseaudio problem. Tried the items I typed out in my first post but none of those worked.

---

### Post by davisond on 2009-11-16
I think it's generally a pulseaudio issue.  Sound is totally borked in Karmic for many, many users (me included) judging by the forums, issue trackers and IRC complaints.  Nor is it the only thing.  I'd recommend Jaunty if you want a working sound setup. :(

---

### Post by isoToxin on 2009-11-16
Have you tried disabling the pulse daemon? Check out this thread.  

[http://ubuntuforums.org/showthread.php?t=1325890](http://ubuntuforums.org/showthread.php?t=1325890)

I had lots of audio issues with pulse running.  Disabling it solved them all, and this method doesn't require you to uninstall/remove anything from your system.

Here is the section showing the method for disabling pulseaudio daemon in karmic:

> Stopped the daemon from ever auto-spawning itself whenever it is killed.

This is done by creating a file called 
client.conf
in the
~/.pulse
folder.

Add a line to this file:
autospawn = no

Once that's done, you should be able to kill pulseaudio by doing:
pulseaudio -k
If the daemon doesn't restart, it's worked.

Then, I moved the following script to my home folder where it was out of the way, so it wouldn't launch pulse at all.

/etc/X11/Xsession.d/70pulseaudio

Once that's moved, pulse should no longer launch when you login.

I then downloaded gnome-alsamixer so that I had an alternative vol control.

Finally, I set my volume levels how I wanted them, then stored them using:

alsactl store

I added a new startup item (system -> preferences -> startup).  The command for this item is:

alsactl restore

This should use the vol levels you stored previously and set them each time gnome starts.

After all this, I'm finally happy with the audio in ubuntu. All this was done without completely removing pulse, and it can be started whenever necessary with

pulseaudio -D

and killed again with:

pulseaudio -k

---

### Post by kschanaman on 2009-11-17
Thanks, IsoToxin, that cleared up the crummy sound. The recording problem is still there, but the playback audio system-wide is 100% better. 

The audacity thing has me bewildered. No matter what input I select, the dB meter shows I'm getting loud noise from my system, while the left and right channels aren't equal. The right channel shows -20 dB worth of noise and the left channel shows -24 dB worth of noise. Both channels show the audio being recorded above the center lines on both channels. I have no such problems when booting this same machine into Windows 7. Looks like ALSA has serious problems with my ALC1200 hardware on the recording side. Plus, I can't record system passthrough audio in Audacity. It's only able to "find" audio when using the Mic, but is unable to record anything else, whether set to "Line" or "CD"  Capture is set to record, but still nothing. 

The use of Ubuntu for the "Studio" part is for naught. May have to investigate other distributions, but the selection is limited when you have a 64-bit machine. Not many distributions out there offer 64-bit performance unless they are derivatives of Ubuntu (i.e. Mint Linux, Kubuntu, Xubuntu, etc.)  I'm certain all distributions based off of Ubuntu are using the same Pulseaudio/Alsa combination. 

Any further ideas? This is meant to be a video documentary production system which requires ability to record WAV, system pass-through audio, as well as a microphone. I dread the idea of using any kind of "Windows" for this purpose. 

Thanks for getting me half-way there! I can now experience sound playback as a "normal" user would.

---

### Post by UnicornsRock420 on 2010-03-04
```
Codec: Realtek ALC1200
  *-multimedia
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
       resources: irq:22 memory:fe024000-fe027fff

```

The audio with the volume cranked is extremely faint, and pulseaudio daemon isn't installed. Tried editing /etc/modprobe.d/alsa-base.conf for the options snd-hda-intel probe_mask=1, still dead in the water:

```
aplay: device_list:223: no soundcards found...
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
[alsa.c:157] error: cannot open device default
[audio.c:631] error: failed to open audio device
[audio.c:179] error: Unable to find a working output module in this list: alsa
[audio.c:533] error: Failed to open audio output module
[mpg123.c:773] error: Failed to initialize output, goodbye.
```Any ideas?

---

