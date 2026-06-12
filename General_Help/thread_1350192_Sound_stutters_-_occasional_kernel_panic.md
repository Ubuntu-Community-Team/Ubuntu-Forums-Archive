---
title: "Sound stutters - occasional kernel panic"
date: 2009-12-09
forum: General Help
---

### Post by hidinginthemountains on 2009-12-09
I think I posted this to the wrong forum initially, and don't know how to move it. :oops:

[http://ubuntuforums.org/showthread.php?p=8467056#post8467056](http://ubuntuforums.org/showthread.php?p=8467056#post8467056)

---

### Post by hidinginthemountains on 2009-12-09
*[I'm closing that other thread cause I think it's in the wrong place, all info here now]*

I recently upgraded from Intrepid to Jaunty. I now have problems with my sound stuttering a bit (ie: while playing music in Rhythmbox, watching/listening to streams in Firefox, watching movies in VLC...etc). Though the problem seems worse at some times then others, I believe that the computer doing "other things" (like a torrent client writing to the disc for example) while I'm listening is what causes it to manifest.

Additionally, at least twice in the last week my laptop has suffered what I assume is a kernel panic (completely locks up, CAPS LOCK blinks). I think this *may* be related.

I'm not sure exactly what information to provide so that folks can help me with this, so to start with I'll throw in the output from [FONT="Courier New"]aplay -l[/FONT]



TIA for any help. Let me know what other info I can provide (log entries? hardware/software configs?).

> :~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
Subdevices: 1/1
Subdevice #0: subdevice #0 
> :~$ lspci -v | grep -i audio
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01) 

++++++++++++++++++++++++++++++++++++++++++++++++
[http://ubuntuforums.org/showthread.php?t=1351573](http://ubuntuforums.org/showthread.php?t=1351573)
++++++++++++++++++++++++++++++++++++++++++++++++
^^^more and better info

---

