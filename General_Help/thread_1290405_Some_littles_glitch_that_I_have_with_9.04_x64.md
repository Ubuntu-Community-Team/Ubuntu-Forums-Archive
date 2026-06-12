---
title: "Some littles glitch that I have with 9.04 x64"
date: 2009-10-13
forum: General Help
---

### Post by Scoubidou on 2009-10-13
Hi,

I've fresh installed 9.04 x64 a few months ago and tuned it to my liking. There is however a few things that I haven't found the anwsers to in the forum.

1. When I watch a video in Full Screen (VLC, Totem, etc) and something happens in the background the image blink and for a second I see my background image. For example if my gmail notfier (firefox extention) pops-ups I'll see my background. Also if I use the multimedia buttons of my keyboard to adjust the volume, it will show my background. Same thing in VLC if I move the mouse and the controls appears, I'll see my background for a second. 

2. In Nautilus the Date Accessed never change. (I have ext4)

3. When I connect remote (using FreeNX) I don't see my customize icons. The rest of my customization (Backgrounds & pointers) are working. 

Any hints to fix those issues would be appreciate :)

Thanks.

---

### Post by hwttdz on 2009-10-13
2 - drive is being mounted with noatime, which prevents updates of access time for every access, because writes are relatively costly operations this can increase the performance of the disk.  If it's more important to have file access times then you should change the mount options, see pysdm and fstab.

---

### Post by DeMus on 2009-10-13
1. I also used to have it. Somehow, probably with some updates, it disappeared. Can't say which updates though. Either the kernel, the video-driver or the media player itself.

---

### Post by hwttdz on 2009-10-13
A thought for 1 is to add the vlc repository, which will get you a more recent release of vlc.  

[http://wiki.flexion.org/UbuntuIntrepidRepositoryConfiguration.html#1.7](http://wiki.flexion.org/UbuntuIntrepidRepositoryConfiguration.html#1.7)

---

### Post by Scoubidou on 2009-10-13
I'll add the repository, but I already have the latest version of VLC. Beside #1 is a glitch I have in every software that I can put in Full Screen. 
I've installed all updates. 
Haven't check for NVDIA drivers in a while. Could it be related to my window manager?

---

### Post by HavocXphere on 2009-10-13
@1: Try changing the video display type in the VLC settings.

But make very sure you remember the original settings cause the others might not work/crash so you'd want to switch back if it doesn't help.

---

### Post by vinutux on 2009-10-13
i think prob related to graphic card driver

---

### Post by Scoubidou on 2009-10-13
Well, I tryed to install the latest driver from the nvidia site and it was a disaster. Had problems loading X, couldn't activate Visual Effects and video was slower. I didn't see the blinking but video quality was bad and choppy. 

Not too sure what to do next...

I want to say again it's **NOT** a VLC problem. It does the same with other players. Otherwise, I would just use another one. I tryed Miro, Movie Player and MPlayer they all react the same way and blink to the desktop (in full screen mode) when I move the mouse or use the sound key on the keyboard.

Any idea ?

---

### Post by vinutux on 2009-10-14
Which graphic card you have ? just googling or search this forum with your graphic card model+ubuntu

---

### Post by Scoubidou on 2009-10-14
Nvidia 8800 GT

I've already made a lot of research but didn't find anything usefull to fix my problem. 

I'm running the version 180 of the driver. Witch is the last one in the repository

---

### Post by Scoubidou on 2009-10-18
bump

---

### Post by vinutux on 2009-10-18
Try ur luck ....disable from System > hadrware drivers restart..

---

### Post by darkstaar on 2009-10-18
This is certainly not specific to your Nvidia driver. I'm experiencing this same quirk with my ATI adapter.

---

