---
title: "USB Media Won't Automount"
date: 2011-07-22
forum: General Help
---

### Post by cwhittier on 2011-07-22
I am running 9.04.

I have replaced /desktop/gnome/session/required_components/panel "gnome-panel" with "avant-window-manager" in gconf-editor because I want gnome's panels disabled. 

That works great, except now USB media will not automount into the /media folder. The settings to automount are set correctly in the apps/nautilis/preferences section.

Help would be greatly appreciated!

---

### Post by thunderbirdje on 2011-07-22
Exactly the same problem here. Although I haven't replaced anything, just installed the updates which popped up through the Update Manager.

I also noticed that every other device like a mouse or a camera connected with a USB cable will mount (only as picture bridge through Shotwell) but not as a disc.

Any SD card inserted in the SD slot gives exactly the same problem like an external hard drive or USB-stick: the light slightly light up, you hear some noise (in case of an external hard drive), in case of a SD card the light flickers shortly HOWEVER the device doesn't automount at all! 

Hope someone can help both of us out! :D

---

### Post by cwhittier on 2011-07-26
After no replies here, and further research, I found a solution that worked for me, however it was slightly complex.

The problem lies in nautilus ending it's process because it sees there  are no windows to be drawn. This means that USB drive insertion will not  be detected.

The solution I used can be found here. It involves creating scripts and  rules, and using udev to the detection and mounting. If you are just  having trouble getting automount to work, and you have not intentionally  stopped nautilus from running, this is probably NOT the solution to  your issue, and you should figure out why nautilus isn't working properly.

[http://superuser.com/questions/53978...t-without-a-us]("http://superuser.com/questions/53978/ubuntu-automatically-mount-external-drives-to-media-label-on-boot-without-a-us")

---

