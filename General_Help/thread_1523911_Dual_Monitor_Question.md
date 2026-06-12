---
title: "Dual Monitor Question"
date: 2010-07-04
forum: General Help
---

### Post by tgeer43 on 2010-07-04
I've hooked up an external monitor to my 10.04 x64 laptop and configured it for TwinView with nvidia-settings. All appears to be working correctly. The only real issue that I'm having is in trying to watch full-screen streaming video in a web browser on the external monitor while working on the laptop's built-in display.
Anytime I click my mouse anywhere on the built-in display, It acts as if ESC had been pressed and the video on the external monitor leaves full-screen mode.

Anyone know of a way around this?

Thanks in advance,

tgeer

---

### Post by Raynman37 on 2010-07-07
I also have this problem and I would like to add another one to this if anyone can answer it: 

I have two monitors side by side and if I have an internet flash video going on the right side and I try to go full screen with it, it goes full screen on the other monitor.

---

### Post by scouser73 on 2010-07-08
I think you need to make one monitor your Primary monitor.

[COLOR="Red"]******[/COLOR]**These instructions will only work for nVidia graphics cards**.

You'll need to do this as root, so follow these instructions.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Click on **X Server Display Configuration**

**3** - Click on the monitor that you wish to make the main monitor

**4** - Check the box stating **Make This The Primary Display For The X Screen**

**5** - Click **Apply**

**6** - Click **Save To X Configuration File** & press **Quit**

***You have now set the login screen to appear on your desired monitor, this will be your main monitor, to change it, just follow the instructions again but this time choosing the other monitor.***

---

### Post by Raynman37 on 2010-07-08
Thanks a bunch, Scouser...it seems to work now!  It took a reboot for the settings to change.

L-I-V, E-R-P, Double-O L, Liverpool FC! 

(I know you're from Liverpool but I don't know if you're an LFC fan...lol)

---

### Post by scouser73 on 2010-07-08
> **Raynman37 said:**
> Thanks a bunch, Scouser...it seems to work now!  It took a reboot for the settings to change.

L-I-V, E-R-P, Double-O L, Liverpool FC! 

(I know you're from Liverpool but I don't know if you're an LFC fan...lol)

Glad to help mate, and yes I support Liverpool lol.

---

