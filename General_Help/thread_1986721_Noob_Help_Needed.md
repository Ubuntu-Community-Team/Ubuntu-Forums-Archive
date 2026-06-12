---
title: "Noob Help Needed"
date: 2012-05-25
forum: General Help
---

### Post by TonyManchester on 2012-05-25
Hi just switch from windows last night and i have no sound i am using HDMI cable which is ATI radeon 
i go to the sound setting and pannel and there is  no hardware box for me to change to HDMi there is only input , output , sound fx , apps

any idea how i can get my audio working?

also is it possible to install virtual dub? i used it on windows for video capture

---

### Post by Zvlwab on 2012-05-25
Open up a terminal and run
```
pavucontrol
```
Does this open up the window you had opened before?
If not, run
```
sudo apt-get install pavucontrol
```
and then run pavucontrol again.

Navigate to Output devices.
You should see your videocard there and make sure it's enabled.
Navigate to Playback
Make sure the program you want to play audio with, uses the HDMI output.

If you don't have any sound you may need to install your video card drivers:
```
sudo apt-get install fglrx-updates
```
Reboot and try again.

---

### Post by TonyManchester on 2012-05-25
thanks worked perfect :) do u know if there is a way to install virtualdub i use it for video capture from my capture card

---

### Post by Zvlwab on 2012-05-26
You shouldn't try to run Windows software in Linux (except for very specific software, such as games).
You should try other software that does the same thing. For example I just found [AviDemux]("http://www.videohelp.com/tools/AviDemux"), but I guess there are many programs that can do the same.

---

