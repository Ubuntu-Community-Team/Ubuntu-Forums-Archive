---
title: "trouble making udev rules"
date: 2012-05-24
forum: General Help
---

### Post by someitalian123 on 2012-05-24
I'm having trouble setting up udev rules to assign my webcam to video0 and my tv tuner to video1. Here's what I have but it doesn't appear to be working

 ```
# /etc/udev/rules.d/10-persistent-video.rules
# 


# Create a persistent name /dev/video0 symlink to the device name assigned by the kernel
SUBSYSTEM=="video4linux", KERNEL=="video*", ATTR{name}=="HD Webcam C525", ATTR{index}=="0", SYMLINK="video0"

# Create a persistent name /dev/video1 symlink to the device name assigned by the kernel
SUBSYSTEM=="video4linux", KERNEL=="video*", ATTR{name}=="ivtv0 encoder MPG", ATTR{index}=="0", SYMLINK="video1"

# Create a persistent name /dev/video25 symlink to the device name assigned by the kernel
SUBSYSTEM=="video4linux", KERNEL=="video*", ATTR{name}=="ivtv0 encoder PCM", ATTR{index}=="3", SYMLINK="video25"

# Create a persistent name /dev/video33 symlink to the device name assigned by the kernel
SUBSYSTEM=="video4linux", KERNEL=="video*", ATTR{name}=="ivtv0 encoder YUV", ATTR{index}=="1", SYMLINK="video33"
```

I named it 25-name-video-devices.rules and moved it to /etc/udev/rules.d but my webcam still shows up as video1 and my tv tuner video0. What am I doing wrong?

---

### Post by someitalian123 on 2012-05-24
I was able to create working system links to use for my tv tuner and webcam with this

# /etc/udev/rules.d/10-persistent-video.rules
# 


# Create a persistent name /dev/video0 symlink to the device name assigned by the kernel
SUBSYSTEM=="video4linux", KERNEL=="video*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="0826", ATTR{name}=="HD Webcam C525", ATTR{index}=="0", SYMLINK+="video100"

# Create a persistent name /dev/video1 symlink to the device name assigned by the kernel
SUBSYSTEM=="video4linux", KERNEL=="video*", ATTR{name}=="ivtv0 encoder MPG", ATTR{index}=="0", SYMLINK="video2501"

# Create a persistent name /dev/video25 symlink to the device name assigned by the kernel
SUBSYSTEM=="video4linux", KERNEL=="video*", ATTR{name}=="ivtv0 encoder PCM", ATTR{index}=="3", SYMLINK="video2502"

# Create a persistent name /dev/video33 symlink to the device name assigned by the kernel
SUBSYSTEM=="video4linux", KERNEL=="video*", ATTR{name}=="ivtv0 encoder YUV", ATTR{index}=="1", SYMLINK="video2503"

---

