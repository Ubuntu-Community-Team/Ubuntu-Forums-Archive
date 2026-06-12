---
title: "OpenGL Error while runing a CS test"
date: 2006-02-19
forum: General Help
---

### Post by Kasuko on 2006-02-19
I get the following error from terminal when I try to run CS walktest
```
kasuko@KaiUbunto:~$ walktest
WARNING: could not load plugin 'crystalspace.font.server.freetype2'
WARNING: could not load plugin 'crystalspace.graphics2d.glx'
Error loading Graphics2D plugin.
WARNING: failed to initialize plugin 'crystalspace.graphics3d.opengl'
ERROR: Console: Unable to locate 3D renderer plugin!
WARNING: failed to initialize plugin 'crystalspace.console.output.simple'
DEBUG: Sound System: Software Renderer Initializing..
DEBUG: Sound System: Configured for driver [crystalspace.sndsys.software.driver.oss]
Sound System: OSS driver for software sound renderer initialized.
WARNING: could not load plugin 'crystalspace.sndsys.element.ogg'
No 3D driver!
crystalspace.system:  No iGraphics3D plugin!
crystalspace.system:  Error initializing system!
Cleaning up...
Segmentation fault

```

I have been through every nvidia walk through and still no help.

My Video card is an Nvidia Geforce 6200 (BFG)

I finnaly got sick of trying makeshift attempts for my specific card. I am really new to linux as a whole and need specific answers because I usually dont know what Im doing anyway. 

Thank Kasuko

P.S. if I need to type anything in terminal can you please put the command so I can copy and paste. Im sick of debugging terminal. That would be a real help Thanks

---

### Post by Jedeye on 2006-02-19
Have you properly installed the newest nvidia drivers? if not I would sugest Automatix... its a really easy way to install a lot of usefull items in ubuntu.

---

### Post by Kasuko on 2006-02-22
I have followed the HOWTO on this forum but I dont think they are installed. There was some command to show what is connected to my computer and it says NVIDIA Corporation NV40? [Unknown nVidia Card]. I dont know what that means but I get the Nvidia Logo on startup (Too L:azy to turn it off)

---

