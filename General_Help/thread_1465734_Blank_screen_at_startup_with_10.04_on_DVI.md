---
title: "Blank screen at startup with 10.04 on DVI"
date: 2010-04-29
forum: General Help
---

### Post by Scoobin on 2010-04-29
I realise there is already a thread on this issue, but that thread is about the release candidate version, so I'm writing to say that this issue is still happening in the final 10.04 release.

The old thread is here, and it provides a background to the problem:
[http://ubuntuforums.org/showthread.php?t=1463294&highlight=dvi](http://ubuntuforums.org/showthread.php?t=1463294&highlight=dvi)

If you don't wish to read the old thread: basically with my system the new 10.04 Lucid Lynx version of Ubuntu does not function with my monitor plugged into the DVI connector. I can use it via the VGA connector, and have installed the OS this way but but this is not ideal - I would like to revert to DVI (digital graphics).

I notice on the existing thread also most users have ATI graphics and someone said it may be a problem with those interfaces, but in my case I have NVidia (7900 GS).

---

### Post by Scoobin on 2010-05-04
I fixed this problem. I tried two things and one of them worked but I'm not sure which it was. 

The first and perhaps most likely one can be found here, as I have encountered it previously:

[http://ubuntuforums.org/showthread.php?t=1403904](http://ubuntuforums.org/showthread.php?t=1403904)
Post #4 on that thread has the solution.

The other thing is I have a monitor where sometimes the DVI fails when changing video driver. My monitor is a ViewSonic VX2025wm and when the DVI fails I need to do the following to get it working again:

1) With the computer on plug both VGA and DVI cables in
2) Turn off computer
3) Remove VGA Cable
4) Disconnected power to the monitor for 5 seconds
5) Restart PC

Hopefully those can be of help to someone.

---

