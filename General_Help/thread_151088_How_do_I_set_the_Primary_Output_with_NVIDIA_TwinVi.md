---
title: "How do I set the Primary Output with NVIDIA TwinView?"
date: 2006-03-27
forum: General Help
---

### Post by BlueGravity on 2006-03-27
](*,) I've been trying all weekend to get my new dual monitor setup working properly. I've got one monitor attached to my graphics cards VGA port and another connected to the DVI port through a DVI-to-VGA converter. Whenever I start X, GDM and GNOME uses the DVI port as the main monitor. I want them to use the one I specify. I tried [Option "ConnectedMonitor" "CRT-1,CRT-0"] but that doesn't switch the primary. The Windows NVIDIA drivers uses the VGA port as primary by default and I can change that through the display settings dialog. Is there a way I can do the same thing through xorg.conf?

On a side note, for some reason my DVI-to-VGA connected monitor always has a strange blue hue to it no matter which monitor I use. Its blue on the console as well. However, the actual VGA port shows up cleanly. ](*,)

---

