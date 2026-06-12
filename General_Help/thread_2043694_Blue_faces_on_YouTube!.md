---
title: "Blue faces on YouTube!"
date: 2012-08-17
forum: General Help
---

### Post by Panawe on 2012-08-17
Anyone know why the faces I see on YouTube are always blue?

Panawe

---

### Post by TenPlus1 on 2012-08-17
The blue tint on youtube is a bug in the nvidia driver while using vdpau's hardware accelerated videos...  One way to fix this is to right click on the video and go into Settings and turn OFF hardware acceleration...

Another way to fix this is to use the hacked/fixed vdpau library by doing the following (at your own risk):

12.04 users can use ppa
 sudo add-apt-repository ppa:tikhonov/misc
 sudo apt-get update
 sudo apt-get install libvdpau1

---

### Post by albandy on 2012-08-17
Or enable html5  on youtube.
[http://www.youtube.com/html5/](http://www.youtube.com/html5/)

---

### Post by Scott Harrison on 2012-08-17
> **TenPlus1 said:**
> The blue tint on youtube is a bug in the nvidia driver while using vdpau's hardware accelerated videos...  One way to fix this is to right click on the video and go into Settings and turn OFF hardware acceleration...

Another way to fix this is to use the hacked/fixed vdpau library by doing the following (at your own risk):

12.04 users can use ppa
 sudo add-apt-repository ppa:tikhonov/misc
 sudo apt-get update
 sudo apt-get install libvdpau1
I fixed this problem without turning off hardware acceleration.

[http://askubuntu.com/questions/117127/flash-video-appears-blue](http://askubuntu.com/questions/117127/flash-video-appears-blue)

---

### Post by Panawe on 2012-08-17
Jolly good, I did the fixed vpau library thing. Now i can see Gotye's flesh tones properly :)

---

### Post by Scott Harrison on 2012-08-17
> **Panawe said:**
> Jolly good, I did the fixed vpau library thing. Now i can see Gotye's flesh tones properly :)
Heh, didn't know he had a fan base in the UK too... He started in a local 60's themed band doing pub shows.

---

