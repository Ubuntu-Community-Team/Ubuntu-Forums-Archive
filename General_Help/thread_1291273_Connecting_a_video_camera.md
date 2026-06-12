---
title: "Connecting a video camera"
date: 2009-10-14
forum: General Help
---

### Post by alan_uk on 2009-10-14
I have a video camera (Canon) which is connected to the  PC via a firewire rather than a USB.  The camera is not picked up.  Is there driver that needs to be installed?

Thanks
Al

---

### Post by StuartN on 2009-10-14
> **alan_uk said:**
> The camera is not picked up.

Apparently you need to sudo modprobe raw1394 dv1394, which is not entirely the friendliest of welcomes to the camera. See [https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire) for full instructions.

---

### Post by KeyserSoze93 on 2009-10-14
Hmm, firewire should would.

What do you mean, it's not detected? What is the result of the command:

```
ls /dev/raw1394
```

If it shows up, the next step is to install a copy of dvgrab (if you have 8.04, it is best to build it from source, which is as easy as getting the packing, apt-get build-dep dvgrab, and ./configure && make && sudo make install), and get grabbing, with a command line like:

```
sudo dvgrab -rewind --autosplit --format raw -|ffmpeg -f dv -i - -target dvd out.mpg
```

The reason to pipe (make sure ffmpeg is installed) is that otherwise you'll end up with a hard drive full of uncompressed video before you've got 5 minutes of footage.

---

### Post by alan_uk on 2009-10-14
Thanks I am using Ubuntu 9.10 Karmic Kaola. I tried ls /dev/raw1394 and it displayed no camera exists

---

### Post by alan_uk on 2009-10-15
Thank you for the help video is captured well using Kino

---

