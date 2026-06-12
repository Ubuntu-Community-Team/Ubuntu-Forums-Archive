---
title: "installed updates and suddenly no sound"
date: 2009-07-06
forum: General Help
---

### Post by over_my_head on 2009-07-06
well, i just installed some updates for ubuntu 8.10 (i'm waiting to upgrade to 9.04) and suddenly my sound doesn't work. the volume control button on my toolbar shows a red x as if on mute but when i click on volume control it says "no volume control Gstreamer plugins and/or devices found"
i tried going to the synaptic package manager and installing all the Gstreamer plugins but that didn't seem to do anything. so then i tried uninstalling all the gstreamer plugins but that only screwed things up worse. now when i try to open volume control it says "Failed to start Volume Control: Failed to execute child process "gnome-volume-control" (No such file or directory)"
please help me before i mess it up worse!

---

### Post by LepeKaname on 2009-07-06
> Failed to execute child process "gnome-volume-control"

What program you use to install software (synaptic, aptitude, apt)?
Try to search in the logs what you installed/removed.

Try to install "gnome-media" and see if that fix it.

---

### Post by over_my_head on 2009-07-07
thank you! that fixed the part i screwed up but it's still telling me there's "no volume control GStreamer plugins and/or devices"

sound was working fine until i installed the latest updates... :-(

oh and i'm using the synaptic package manager for install/removal.

---

### Post by LepeKaname on 2009-07-07
Check this page:

[http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/](http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/)

---

### Post by Soul-Sing on 2009-07-07
try : ```
sudo apt-get install linux-ubuntu-modules-`uname -r`
```
when it is allready installed nothing happens. I solved this way having tthe same error: "no volume control GStreamer plugins and/or devices"

---

### Post by over_my_head on 2009-07-08
i tried the command: sudo apt-get install linux-ubuntu-modules-'uname -r'
and this is what i got:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-ubuntu-modules


---

### Post by michy99 on 2009-07-08
Make sure you use back-ticks (`) and not single quotes('). Try copy and paste from leoquant's post.

---

### Post by over_my_head on 2009-07-08
oops, i think i did use single quotes. so i just tried copy & paste and now it says:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-ubuntu-modules-2.6.27-14-generic



edit: I just ran "aplay -l" and it says there are no sound cards found... what the heck?

---

### Post by over_my_head on 2009-07-11
the 'no gstreamer plugins' error was resolved by upgrading Alsa following the instructions on this thread: [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

my sound is back! i am much indebted to the people on this forum. :-)

---

