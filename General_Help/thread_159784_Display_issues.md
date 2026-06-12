---
title: "Display issues"
date: 2006-04-13
forum: General Help
---

### Post by jbcbussoft on 2006-04-13
I have loaded Ubuntu 5.04 for Intel x86. I loaded it as a virtual pc in Microsoft's Virtual PC 2004. Everything works well until the login screen appears. I can't read it. I recognize what it is but the fonts/graphics are displayed at a low level. The virtual machine properties indicate that the screen resolution is 1600x600x6. Is there a way to change the screen resolution at the command line before it gets into the gui interface?

---

### Post by aysiu on 2006-04-13
Are you using a live CD? If so, type ```
boot vga=791
``` at the beginning instead of just hitting return.

Otherwise, press Control-Alt-F1, log in and type ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by jbcbussoft on 2006-04-13
Aysiu, I took your advice and was able to run through the setup again, however, I still have the same problem. On the setup screen that deals with the different resolutions to display, the only settings that were checked were 640x480, 800x600 and 1024x768. I put a 19" screen on the pc and was able to get a better image. I can sort of see what I am doing. If you can tell me how to change the screen resolution from with in the system I will try that.

---

