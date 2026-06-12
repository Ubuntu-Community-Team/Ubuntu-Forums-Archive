---
title: "Video playback is choppy?"
date: 2011-02-18
forum: General Help
---

### Post by Xecutor13b on 2011-02-18
I verified that the choppy videos on my pc is strictly an Ubuntu problem as I dual boot with Windows XP and XP videos play perfect. Does anybody know how to manually download the latest nvidia drivers for Ubuntu or maby point me to the right thread? Not 100% sure the gpu driver is the problem, but if anybody else has any ideas ill appreciate it

---

### Post by Bigtime_Scrub on 2011-02-18
In order to help you we may need a little more information. Do you have Ubuntu-Restricted-Extras installed? What format is the video in?

---

### Post by mikewhatever on 2011-02-18
Downloading the latest nvidia driver (not sure why you want many) should be easy. Head over to nvidia.com, click Download.

---

### Post by 3rdalbum on 2011-02-18
> **mikewhatever said:**
> Downloading the latest nvidia driver (not sure why you want many) should be easy. Head over to nvidia.com, click Download.

It's not so easy to install; I wouldn't recommend it.

You should have a look in your video player's settings to see what video output option you are using. If you have the Nvidia driver installed, you can use the "XVideo" output module, or (even better) the "VDPAU" module.

Also, if you have choppy video, try running without "visual effects" turned on - since you're using Lubuntu you probably aren't using Compiz or any other visual effects window manager, but it's worth mentioning just in case you are.

---

### Post by Xecutor13b on 2011-02-19
> **Bigtime_Scrub said:**
> In order to help you we may need a little more information. Do you have Ubuntu-Restricted-Extras installed? What format is the video in?


Yes I do. I actually tried downloading the latest nvidia drivers just now, and it says in the terminal that the newest version is already installed. I even tried updating opengl, and it says again, "newest version is already installed. Maby choppy is the wrong way to describe what im talking about, but the video looks kinda broken up?

Like during action scenes or fast movements, the video will look broken up, but still play at full speed. I played the same video on Windows Xp on youtube in 1080P as I did in Ubuntu, and on XP it played perfect, but on Ubuntu, it didnt looks so good.

Here is a video of what im talking about.
_[http://www.youtube.com/watch?v=3aQ-AOGhPFc](http://www.youtube.com/watch?v=3aQ-AOGhPFc)_

See how the video looks kinda broken up at times?  I dont know how to describe this, I really hope somebody can help me figure out why this is happening

---

### Post by wojox on 2011-02-19
Sounds more like a flash problem. See the link in my signature.

---

