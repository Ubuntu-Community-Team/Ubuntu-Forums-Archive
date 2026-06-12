---
title: "DVD drive spins down during playback, leading to stuttering video"
date: 2006-06-29
forum: General Help
---

### Post by droazen on 2006-06-29
When I play a dvd in dapper, it plays perfectly fine for the first several minutes, but at some point the drive spins down, and the frame rate drops to ~1 frame every 2 seconds. This happens in both xine and mplayer. If I then seek to another point in the title, the drive spins back up & everything is ok again for another few minutes.

I suspect that the solution will require me to edit /etc/hdparm.conf to change the settings for the drive (since it doesn't seem to be the fault of either xine or mplayer), but I'm not sure what setting(s) to add/change. I don't want to disable spindown completely, I only want to disable it when there's disc activity.

Here is the output of hdparm on the drive:

```

$ hdparm /dev/hdc

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

```

Any help is much appreciated :)

---

### Post by falcon15500 on 2006-06-29
Tha man page for **hdparm** advises that the **-S** option is used to control the spindown time for drives.  0 is no automatic spindown.  1 to 240 specify multiples of 5 seconds, so 5 seconds to 20 minutes.  Above that and the times get rediculous. ;)

Try using a value of 120 perhaps, and see how it goes.

falc

---

