---
title: "Red missing video playback"
date: 2010-04-13
forum: General Help
---

### Post by rapattack1 on 2010-04-13
Hi for some reason when i play videos i have either downloaded(youtube/facebook whatever) that are on the hard drive or stored on cd's for the last day or so they are missing the colour red. They are very greeny. I don't think i did anything to make this happen. I did an apt-get update/upgrade after this thinking that there might be a fix but it is still the same. I tried VLC and Totem and it is still the same. What could be the problem?:confused:

---

### Post by 3rdalbum on 2010-04-14
Nvidia sometimes introduces this problem in its drivers. The usual workaround is to change the video output module that your video players use; for instance, if you go into VLC's preferences, go to the Video tab, and you can change the output module to "X11".

---

### Post by rapattack1 on 2010-04-14
Hi i can't see the video output under the video tab. This is a new area for me .

---

### Post by rapattack1 on 2010-04-27
:popcorn: Please help!!! I will shout the popcorn lol

---

### Post by gradinaruvasile on 2010-04-27
Do you have nvidia card with the restricted drivers?

Then launch nvidia-settings in a terminal (not with sudo) and check the "Xserver xvideo settings tab". See if every value is at 0.

Ati cards have something similar, called the catalyst control center or something.

Also, both totem and vlc have their own color correction methods.

Totem: edit -> preferences -> display
Vlc :  open vlc then press ctrl+e

Check those too.

---

### Post by rapattack1 on 2010-04-27
I have had so many installs of Ubuntu i don't remember if i have those drivers. I have a nvidia card that is for sure. I know there was some confusion with this install but i can't remember wether i was told it was automatically included???
I didn't have nvidia-setting installed so i did so via the terminal and when i run it i get this:
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

I went into both Totem and vlc but can't see what to change. This is a field i know nothing about. If your saying i have to add red somehow i can't see red or any other colour mentioned so I don't know what to do.

In the nvidia-settings there was nothing with numbers so i have no idea about that either.

---

### Post by rapattack1 on 2010-05-02
Yippe i found the solution. It is the hue, saturation and contrast that have to be adjusted ....that did the trick!!!:P

---

