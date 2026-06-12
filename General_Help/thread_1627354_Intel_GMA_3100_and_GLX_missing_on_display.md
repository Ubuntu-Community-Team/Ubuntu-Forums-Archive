---
title: "Intel GMA 3100 and GLX missing on display"
date: 2010-11-21
forum: General Help
---

### Post by sauronnikko on 2010-11-21
Hello. I have a NVIDIA graphic card which became damaged yesterday. I had to remove it and now I'm using my Intel GMA 3100 which came with the motherboard. Everything works fine, but when I try to run a program I made in OpenGL, I get the following error:

```

Xlib:  extension "GLX" missing on display ":0.0".
freeglut (./proy2): OpenGL GLX extension not supported by display ':0.0'

```

Where proy2 is the app I'm trying to run. Thanks for your help!

---

### Post by dcstar on 2010-11-22
> **sauronnikko said:**
> Hello. I have a NVIDIA graphic card which became damaged yesterday. I had to remove it and now I'm using my Intel GMA 3100 which came with the motherboard. Everything works fine, but when I try to run a program I made in OpenGL, I get the following error:

```

Xlib:  extension "GLX" missing on display ":0.0".
freeglut (./proy2): OpenGL GLX extension not supported by display ':0.0'

```

Where proy2 is the app I'm trying to run. Thanks for your help!

Linux does not have 3D drivers for that card. Nvidia and ATI chips have 3D drivers.

---

