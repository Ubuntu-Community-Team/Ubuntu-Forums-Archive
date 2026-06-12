---
title: "Was my kernel compiled with this config item?"
date: 2009-11-16
forum: General Help
---

### Post by Nicholas Escalona on 2009-11-16
I'm trying to make Flash work with Video for Linux 2. I have heard about the Flashcam project, but the source won't compile for me.

I suspect my kernel wasn't compiled with the CONFIG_VIDEO_V4L1_COMPAT configuration item. This is a stated prerequisite for compiling Flashcam. It's the only prerequisite that I'm not sure I've got.

How can I check that? I have not compiled my own kernel.

Thanks folks.

---

### Post by Ilalmi on 2009-11-16
Hi,

lsmod shows what kernel modules are currently loaded. 
```
lsmod | grep v4l1
```

As your kernel's configuration options are written to a file called /boot/config-[your kernel],
you could also use ```
cat "/boot/config-`uname -r`" |grep VIDEO_V4
``` to see, if the option you are looking for is enabled.

---

### Post by Nicholas Escalona on 2009-11-16
Thanks. The two outputs I get are
```
v4l1_compat            14496  2 uvcvideo,videodev
```
```
CONFIG_VIDEO_V4L2_COMMON=m
CONFIG_VIDEO_V4L1_COMPAT=y
CONFIG_VIDEO_V4L2=m
CONFIG_VIDEO_V4L1=m
```
So it is enabled. The question is, why can't I compile Flashcam? They state the requirements as >     * Kernel 2.6.11
    * Kernel headers needed
    * Kernel compiled with CONFIG_VIDEO_V4L1_COMPAT
    * Dev tools (gcc, make, etc).
    * System with udev running 
I'm 85% sure I've got all of these, and I've checked with Synaptic. When I compile, I get this.
[http://pastebin.com/m4567b0ad](http://pastebin.com/m4567b0ad)

---

### Post by Ilalmi on 2009-11-17
There seems to be a problem with compiling vloopback under ubuntu > 8.04: [http://ubuntuforums.org/showthread.php?t=950852](http://ubuntuforums.org/showthread.php?t=950852)

There's a flashcam ppa for karmic. Have you tried that? 
[https://launchpad.net/~irving-popovetsky/+archive/ppa](https://launchpad.net/~irving-popovetsky/+archive/ppa)

---

### Post by Nicholas Escalona on 2009-11-17
Ah! I hadn't found that. Installation went fine. Only now, I get this.

```

nicholas@nicholas-laptop:~$ flashcam
Scanning devices
------
Found V4L2 Capture device: /dev/video0 (uvcvideo/Built-in iSight)
Found V4L Video loopback input: /dev/video1
------
Forwarding frames from /dev/video0 to /dev/video1
Input device: /dev/video0
VIDIOC_S_FMT error 22, Invalid argument
nicholas@nicholas-laptop:~$ 

```

I've already loaded the vloopback driver with "flashcam -L".
VIDIOC_S_FMT is a call associated with V4L2. It's supposed to decide the width and height of the output video. This makes sense, because according to the Flashcam site, the next line flashcam prints to stdout should be of the form "Size = 160 x 120". So, somehow the driver is failing at deciding what size to use.

The exact same thing happens if I try to pass the size manually, with "flashcam -s 320x240".

This has really diverged from the thread title. :/ Thanks for your help so far! :P

---

### Post by Ilalmi on 2009-11-20
It works flawlessly for me. I haven't the faintest idea what could cause error 22, sorry. I wasn't even able to find a description of the error codes somewhere.

Can you try another cam? Maybe V4L2 doesn't work out of the box with your MacBook cam?

---

### Post by Nicholas Escalona on 2009-11-22
I don't have any webcams besides my Macbook's internal iSight. I'll try asking around at the flashcam forums. Thanks for your assistance.

---

