---
title: "I have no audio"
date: 2009-08-09
forum: General Help
---

### Post by emid on 2009-08-09
So ever since about a week ago, I have had no audio in Ubuntu whatsoever.  I don't even get the little drumroll sound when gdm first loads up.  Unfortunately for me I had several things happen to my system almost at once, so it has made it a little more difficult for me to isolate the original cause of this problem.

The audio seemed to stop working after a reboot where I had installed some updates.  If I look at the Volume Control it just says "Null Output (PulseAudio Mixer)"

I also had an issue where someone vacuumed near my computer and the static electricity killed my video card.  I swapped the card out with a new GEForce 9800 Pro and I was back up and running.  I'm pretty sure the sound worked for a few days after the video card / static electricity incident, so I'm inclined to believe that's probably not the cause.

I booted into the Ubuntu live CD and I don't have any sound there either.  I don't remember if I used to have sound when in the live CD, so I'm not sure what that determines if anything at all.  

Can anyone help me out here with some guidance or suggestions?  Having no sound is starting to be incredibly annoying.

---

### Post by martinbaselier on 2009-08-09
First start troubleshooting:

Please paste the output of: 

**sudo lshw -c multimedia**

---

### Post by emid on 2009-08-09
Here it is:
```
*-multimedia            
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0

```

---

### Post by emid on 2009-08-09
Also, I should note that in my quest to get audio back I happened upon a link in the forums here that said that I should install the following:

```
gnome-volume-control-pulse gnome-alsamixer alsa-oss ubuntu-restricted-extras vlc-plugin-pulse libsdl1.2debian-all asoundconf-gtk xmms2-plugin-pulse padevchooser
```

And that I should make sure that root and my user were both members of the groups "pulse, pulse-access, pulse-rt"

While this didn't work (I actually now have two volume control icons on my panel), I'm noticing that after rebooting my system actually seems to recognize that I have some kind of audio device. For instance aplay -l yields:

```
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

where before it wouldn't show anything.

---

### Post by martinbaselier on 2009-08-09
Your soundcard is recognised and there is a driver loaded.

In a terminal run:
alsamixer

Check if all volumecontrols are open and nothing is muted.

Then use 
aplay test.wav 
I hope you have a wav file somewhere on your system. Replace test.wav with the name of the file. 

(aplay only works with wav, voc, raw and au)

Personally I try to avoid pulse as much as possible. You don't really need it.

---

### Post by emid on 2009-08-09
Ok, so I ran alsamixer and put the volume up on pretty much everything I could. I downloaded a wav file and tried to play it.  It looked like it was playing but I couldn't hear anything.

---

### Post by emid on 2009-08-09
Having two volume icons in the panel was annoying me so I removed the extra one with:
```
sudo apt-get remove gnome-volume-control-pulse
```

After I rebooted I see now that the system once again doesn't recognize my onboard audio.  

"sudo lshw -c multimedia" doesn't return anything.

I reinstalled the gnome-volume-control-pulse but I still have nothing coming up now.  I don't know if that is just a coincidence or actually a result of removing that package.

---

### Post by emid on 2009-08-09
If this cannot be resolved easily, is it at least something that will be remedied by a fresh reinstall?  I really would rather not do that but I don't want another week of no audio either.

Does the fact that I didn't have audio when I booted from the live cd indicate that I won't have audio after a fresh install?  I've been using Ubuntu with this motherboard for the last three releases without issue, I wish I knew why this suddenly started up now.

EDIT:

Just to clarify, I've been using 9.04 with this hardware with no problems related to audio for a few months.  It's not like I just upgraded recently and then found out my audio didn't work.  Something clearly had to have changed recently for this to occur.

---

### Post by JC Cheloven on 2009-08-09
Possible hint: do you dual boot? Does sound work with windoze (tm) or with other linux distro (I'd suggest mandriva or mint for live cd mode). If it doesn't, it is obvious to suspect from a hardware problem.

If it does work, I'd go reinstall. I've never been able to solve a single sound problem with pulseaudio being around.

---

### Post by emid on 2009-08-09
Unfortunately, no I'm not dual booting so I don't have a Windows install to compare it to.  I had been thinking the same thing earlier.  I really wish I could remember if I used to be able to get audio when in the live cd (my inclination is yes, but I'm not certain).  It just seems weird to me that it would be a hardware issue because it worked for at least a week after the the supposed static electricity incident.  But who knows, stranger things have happened I suppose.

I may have to repartition my boot drive to make room for a windows install to test it out.  Although, I've pretty much backed up all my configs and my data is on a separate drive, so reinstalling Ubuntu wouldn't be the end of the world.  I was just hoping that I could resolve this in a lazier fashion. :)

---

### Post by nikhilbhardwaj on 2009-08-10
hi sorry to barge into this thread
i too have no audio

here's the output of sudo lshw -c multimedia
```
nikhil@bhardwaj:~/Sources/opera-9.64$ sudo lshw -c multimedia
  *-multimedia            
       description: Multimedia audio controller
       product: VT8233/A/8235/8237 AC97 Audio Controller
       vendor: VIA Technologies, Inc.
       physical id: 11.5
       bus info: pci@0000:00:11.5
       version: 30
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
```

---

### Post by luangwa on 2009-08-10
I do not have audio as well. Here is my troubleshooting trace:
 *-multimedia            
       description: Multimedia audio controller
       product: [SB Live! Value] EMU10k1X
       vendor: Creative Labs
       physical id: 9
       bus info: pci@0000:02:09.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=EMU10K1X latency=64 maxlatency=20 mingnt=2 module=snd_emu10k1x

I've been to Pulse-Audio listing at Wiki and no audio at all. I have documented all the tests, modification, changes that I have tried but to no avail. I was so frustrated trying to solve this problem that I removed Jaunty and install Intrepid hoping that would solve the problem but it didn't. Maybe I should go back to Hardy Heron. 

Pulse-Audio might be great but it isn't newbie friendly.

Help!(*,) Can I get sound if I totally remove Pulse-Audio and use Alsa only?
If so how to I go about doing this cleanly. 

Thanks for your anticipated help.](*,)

---

