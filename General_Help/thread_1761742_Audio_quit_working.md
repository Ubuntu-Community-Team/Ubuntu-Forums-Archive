---
title: "Audio quit working"
date: 2011-05-18
forum: General Help
---

### Post by OldManRiver on 2011-05-18
All,

My audio on one Ubox quit working.  Was following thread on this at:

[http://ubuntuforums.org/showthread.php?t=725945&](http://ubuntuforums.org/showthread.php?t=725945&)

When I issue the commands:```
aplay -l
lspci -v | grep -i 'audio'
```I get the following:> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@tc-noc-server:/etc/samba# lspci -v | grep -i 'audio'
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
Not sure what my next step is?  lshw shows it this way:>  *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:e400(size=256) ioport:e080(size=64) memory:ffa7f800-ffa7f9ff memory:ffa7f400-ffa7f4ff
All the alsa and alsaplayer apps show installed in Snaptic Package Manager.

All help appreciated!

Thanks!

OMR

---

### Post by OldManRiver on 2011-05-19
All,

OK did a re-install on all the alsa components and ran system test on audio, got very faint sound and found "alsa mixer" had most items muted and volume at minimum.  I reset this but found with logoff/logon that it keeps going to this muted/min state.

What I need now is a HOWTO on setting these startup parms for alsamixer to the preset levels I want.

Thanks!

OMR

---

### Post by OldManRiver on 2011-05-21
All,

Can I get some help so I can close this?

Thanks!

OMR

---

### Post by OldManRiver on 2011-06-04
All,

The command:

sudo gnome-volume-control

will let me set things once X11 is up, and now I get the Ubuntu theme on boot, but X11 inits and always sets the volume at "mute".

There must be a place in either the X11 or the gnome setting where I set these values permanently.

Does anyone know where?  Would this be somewhere in the USER settings?

All help appreciated!!

Thanks!

OMR

---

