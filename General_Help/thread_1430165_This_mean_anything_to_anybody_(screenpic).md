---
title: "This mean anything to anybody? (screenpic)"
date: 2010-03-15
forum: General Help
---

### Post by Moozillaaa on 2010-03-15
Help?

I can't boot any kernels now, even old ones...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=150180&d=1268633057[/IMG]

---

### Post by CompyTheInsane on 2010-03-15
It means the 'nv' driver for xorg is missing

See if package xserver-xorg-video-nv is installed
```

dpkg -s xserver-xorg-video-nv | grep Status

```

---

### Post by jediborger on 2010-03-15
Well basically it's saying it can't find the 'nv' driver. I see you get a command line so let's try something simple before doing too much else. Type the following command in, it will rename the xorg.conf file and if all goes well Ubuntu will generate a new one when you restart.
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then you can restart by:
```
sudo shutdown -r now
```
Hopefully the new generate configuration will work for you, otherwise post back.

---

### Post by Moozillaaa on 2010-03-15
This package was not installed. I installed it.

Then I tried startx, and framebuffer error error comes up.

Will follow your post shortly there jedi...

What about the framebuffer?


edit:
I'm reconfiguring xserver-xorg.... (another machine)

---

### Post by Moozillaaa on 2010-03-15
I got X server back, I forget which kernel I booted.

First I used framebuffer 'yes', didn't work. Then used framebuffer 'no', and got X.

Low resolution - working on it...

---

### Post by Moozillaaa on 2010-03-15
Screen resolution is at 2x4...

Screen Resolution setting is gone from System/Preferences menu.

I see System/Preferences/Display. ???

I have not enabled Hardware driver/nVidia Accel graphics driver. Should I? This is where the problem started at update 3 hours ago...

---

### Post by CompyTheInsane on 2010-03-15
Given how more functional the official nVidia driver is (accelerated 3D and 2D) compared to 'nv', there shouldn't be much of a problem with enabling it.

However. if you prefer to go the open source route, you can remove the 'nv' driver and go with Nouveau (xserver-xorg-video-nouveau) instead. It's an open-source driver for Nvidia cards that aims to provide accelerated 2D and 3D functionality. It isn't complete though. [More details here](http://nouveau.freedesktop.org/)

---

### Post by Moozillaaa on 2010-03-15
> **compugeek32 said:**
> Given how more functional the official nVidia driver is (accelerated 3D and video) compared to 'nv', there shouldn't be much of a problem with enabling it.

Got resolution back, prop driver installed.

Good call checking package installation (I thought I had already [IMG]http://ubuntuforums.org/images/icons/icon5.gif[/IMG] )

---

### Post by Moozillaaa on 2010-03-16
My X-server is re-starting randomly.

Any ideas? (I started an upgrade failure thread, and linked here, in case the answer is in upgrade boards...)

---

