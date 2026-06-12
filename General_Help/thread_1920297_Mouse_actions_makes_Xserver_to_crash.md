---
title: "Mouse actions makes Xserver to crash"
date: 2012-02-04
forum: General Help
---

### Post by Darkfirephoinix on 2012-02-04
Hellos Ubuntu community, I need (really need it) help to work around a problem I have encountered; 
 
I was testing some application on my laptop and it turned out it was unstable with the propietary drivers, so I removed them and did what I had to do. I reinstalled the drivers when I was done working and checked for updates a few hours later, some xorg plugins showed up and I installed them without second thought (yes, that was a very bad idea) then kept working normal and  went to bed, next day I logged in and used the touchpad just to find a terminal screen flashing and being back at the log in screen, after some time I noticed that moving or clicking the mousepad or mouse kills xserver (the same way as ctrl+alt+backspace) 



Thanks in advance for any help.;)

---

### Post by diurnambule on 2012-02-06
Hello.

Same issue for me. After X11 update (I don't know which, but my xorg.conf has been commented out with something like "commented out by update-manager, HAL is now used and auto-detects devices"...

Please help

---

### Post by fitngs on 2012-02-06
[http://askubuntu.com/questions/101308/xorg-segmentation-fault-seems-to-be-relevant-to-evdev](http://askubuntu.com/questions/101308/xorg-segmentation-fault-seems-to-be-relevant-to-evdev)

```
sudo aptitude install xserver-xorg-core=2:1.10.4-1ubuntu4
```> **diurnambule said:**
> Hello.

Same issue for me. After X11 update (I don't know which, but my xorg.conf has been commented out with something like "commented out by update-manager, HAL is now used and auto-detects devices"...

Please help

---

### Post by Darkfirephoinix on 2012-02-06
> **fitngs said:**
> [http://askubuntu.com/questions/101308/xorg-segmentation-fault-seems-to-be-relevant-to-evdev](http://askubuntu.com/questions/101308/xorg-segmentation-fault-seems-to-be-relevant-to-evdev)

```
sudo aptitude install xserver-xorg-core=2:1.10.4-1ubuntu4
```

Thanks for the answer, I found another way to solve this, just removed unity-2d daily repositories and the problem was gone, but i will re-add the repositories and try your work around.

Thanks!

---

