---
title: "I wish my sound would work well"
date: 2010-07-09
forum: General Help
---

### Post by [CS]LaBrute on 2010-07-09
I'm new to this forum and Ubuntu + Gnome, but not so new to Linux, so I am aware of some stuff under linux hood, but still I cannot get some of the things done.

This topic is long and some of you will not have the patience to read it, but here I need the help of the guys that are really familiar with Ubuntu and Gnome. In Debian + KDE this worked without any problem, therefore I assume it is something specific to Ubuntu / Gnome.

Here is what I have: 

- Ubuntu 9.10 (up to date since a few weeks ago)

- Digital + analog output sound card (aplay -l output):
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```- I usually use Firefox/Flash player, Tvtime, Audacious2

- All volumes in Gnome Alsamixer are up and unmutted

- File ~/.asound.rc looks like:
```
pcm.!default {

type hw
card 0
device 1
}
```- It used to look like bellow up until a few minutes ago and it also worked (for everything except Flash player). After setting it to the above content I noticed that on the digital output the sound card is no longer playing Dolby sound like it used to do with the bellow content. Originally, after I first installed Ubuntu this file did not exist and I had no sound on the digital output at all.
```
pcm.!default {
    type plug
        slave {
        rate 48000
        pcm "spdif"
    }
}
```- I do **not** have a file /etc/asoundrc.conf

Here is what I cannot get done: my sound ... it works in a few undesired ways:

[SIZE=5][COLOR=Red]A.[/COLOR][/SIZE] **Flash player (in Firefox) no longer has sound**. Not on the digital and not on the analog output.

At some point today I stumbled into a topic somewhere that suggested to install the following
```
sudo apt-get install flashplugin-nonfree-extrasound
```I did it, it worked, but after a restart the Flash player has no sound again.

The volume in the player is at max and unmuted, so no problem here.

Flash player used to have sound up until a few days ago, but it suddenly does not have sound any more. The system is in the same state since a few weeks (no apt-get update / upgrade during this period).

[SIZE=5][COLOR=Red]B.[/COLOR][/SIZE] **Some of the applications are outputed on the digital output and some on the analogue output**. I wish they all would be on the digital one. For instance VLC / Audacious are outputed on the digital interface while Flash player (at the time it worked) was outputed on the analogue interface.

TvTime is always outputed on the analogue interface, but this is because my TV card works via the line in. This is normal to work this way and I have nothing against it.

What I want is to make all sound (except for TvTime of course) to be outputed on the digital interface. Is this possible?

[SIZE=5][COLOR=Red]C.[/COLOR][/SIZE] **Gnome Alsamixer never remembers the way I leave the volumes after a log out**. I tried
```
sudo alsactl store 0
```but still after each log in I find it muted on Master and the volume at min.

Is there a more "smart" or suitable GUI volume control that would be recommended to me?


Help is appreciated!
Thank You!

---

### Post by lidex on 2010-07-09
Flash/Firefox:
[http://ubuntuforums.org/showthread.php?t=1455816]("http://ubuntuforums.org/showthread.php?t=1455816")

Save volume settings:
Open this file for editing:
```
gksudo gedit /etc/pulse/default.pa
```
Scroll down to this line:
```
load-module module-device-restore
```
Comment it out so it looks like this:
```
#load-module module-device-restore
```
Save. Close. Logout/in.

No help? Comment out line 372 in /etc/init.d/alsa-utils
Should look like this when you're done:
```
# mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1
```

---

### Post by [CS]LaBrute on 2010-07-10
Back with updates:

- Commenting 
**#load-module module-device-restore**
did the trick, the volumes are remembered.

- Flash sound seems to be back after applying the fixes specified here: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

- Everything seems to be outputed on the digital interface now

- I noticed that Dolby capabilities are missing, may be it is something related to fix form the link above applied for Flash. I'll have to do some more digging here, but for now I am satisfied :)

Thanks for the help, you made me a happy person :)

---

### Post by [CS]LaBrute on 2010-07-10
Some more updates:

- Settings in file /etc/asound.conf are "overwritten" by settings in file ~/.asoundrc if this last file exists.

- Sound works fine if the contents of the above file(s) is like bellow, but Dolby capabilities are not working (for digital interface)
```
pcm.pulse { type pulse }
ctl.pulse { type pulse }
pcm.!default { type pulse }
ctl.!default { type pulse }

```- If the contents of the above file is changed to what is bellow then Dolby capabilities are available, but Flash sound in Firefox is lost
```
pcm.pulse { type pulse }
ctl.pulse { type pulse }
pcm.!default {
    type plug
        slave {
        rate 48000
        pcm "spdif"
    }
}
ctl.!default { type pulse }

```I'm not much of a knower of the audio software in Linux, but from what I understood Pulse is a sound support software like ALSA. 

From what I noticed above if I use Pulse, Flash sound is ok, but no Dolby support. On the other hand if I use ALSA, Dolby is ok, but Flash is not ok because it outputs via Pulse ... is this assumption right? 

If it is correct wouldn't I be better off without Pulse at all? Because using ALSA Dolby would work and since Pulse will be no more then may be Flash would understand and try to use ALSA to "speak"? On the other hand this might be a stupid assumption :D

---

