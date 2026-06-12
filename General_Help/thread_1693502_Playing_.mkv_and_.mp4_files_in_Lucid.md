---
title: "Playing .mkv and .mp4 files in Lucid"
date: 2011-02-22
forum: General Help
---

### Post by Endymion689 on 2011-02-22
Basic spec information:

Model: Asus Eee PC 1201HAB
Processor: 2x Intel(R) Atom(TM) CPU Z520 @ 1.33GHz
Memory: 1016MB
Operating System: Ubuntu 10.04.2 LTS
Video: Intel Graphics Accelerator 

Will provide additional information if needed.


Issue: Despite all the legwork I've been doing, I cannot play .mkv and .mp4 files. So far I've tried using VLC player, installing the w32codecs using medibuntu, installing the ubuntu-restricted-extras package, and did some gstreamer stuff. Nothing has worked so far. The best I've gotten is a blank screen with the audio. That's it. Your help would be very much appreciated. 

On a not so serious note, I have also been having trouble getting my webcam to work. I installed cheese, but it too only gives me a blank screen. In spite of having a blank screen, the pictures I take with it show up in the file. It's a rather vexing matter, but not as serious as the above one.

---

### Post by NightwishFan on 2011-02-22
Go into vlc preferences and tell it to use x11video instead of xvideo or automatic. See if that works.

---

### Post by Endymion689 on 2011-02-22
Thanks a lot man, that did the trick in both cases. I wonder if there's a fix like that within Movie Player too. I've added a ton of codecs so everything should work there in theory, but its not a big deal. Now all that needs fixing is my camera issue.

---

### Post by NightwishFan on 2011-02-22
Press alt+f2 and type: gstreamer-properties. Change the video to x11video as in vlc, then totem should work. As for the camera, I have no idea.

---

### Post by Endymion689 on 2011-02-23
Your suggestion worked, but the videos are very choppy in Movie Player.

---

### Post by cascade9 on 2011-02-23
Dont be suprised that videos are choppy. The atoms havent got much power, and most of the .mkv files I see are fairly big (resolution). 

BTW, its not 2 x atoms, its single core CPU with hyperthreading making it look like its got 2 cores.  Also, 1016MB RAM? You might only have 8MB (or less) alocated for video, that wont be helping the video issues.

---

### Post by NightwishFan on 2011-02-23
Not to mention switching to x11video uses all cpu I believe. This issue might be resolved in a future Ubuntu release.

---

