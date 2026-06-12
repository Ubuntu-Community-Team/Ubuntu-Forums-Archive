---
title: "VNC Problem"
date: 2010-06-15
forum: General Help
---

### Post by cd1zz on 2010-06-15
My Ubuntu 10.04 box is running vino vnc server. Here is my strange problem.....

When I try to connect to the Ubuntu box from another computer using any VNC viewer, I get prompted for my VNC password and type it in. The remote screen shows up and everything appears to be working. However, when I start clicking around, nothing on the screen changes. At first I thought the mouse and keyboard inputs were disabled but they were not. I put both computers side by side and could watch the mouse from my viewer machine moving around on the Ubuntu box. So, it appears that as soon as I connect, I get a static image, none of the video is changing on my viewer machine. I have tried both Real VNC viewer and Tight VNC viewer. I also tried using a different VNC server, TightVNC on the Ubuntu box, same problems. Any ideas?

---

### Post by an0dos on 2010-06-15
> **cd1zz said:**
> My Ubuntu 10.04 box is running vino vnc server. Here is my strange problem.....

When I try to connect to the Ubuntu box from another computer using any VNC viewer, I get prompted for my VNC password and type it in. The remote screen shows up and everything appears to be working. However, when I start clicking around, nothing on the screen changes. At first I thought the mouse and keyboard inputs were disabled but they were not. I put both computers side by side and could watch the mouse from my viewer machine moving around on the Ubuntu box. So, it appears that as soon as I connect, I get a static image, none of the video is changing on my viewer machine. I have tried both Real VNC viewer and Tight VNC viewer. I also tried using a different VNC server, TightVNC on the Ubuntu box, same problems. Any ideas?

Try disabling desktop effects on the remote system.

BTW, VNC is very insecure. You should either tunnel it through SSH or use [FreeNX]("https://help.ubuntu.com/community/FreeNX").

---

### Post by CharlesA on 2010-06-15
> **an0dos said:**
> Try disabling desktop effects on the remote system.

This will fix the problem. Desktop effects are a bit much for VNC to handle.

---

