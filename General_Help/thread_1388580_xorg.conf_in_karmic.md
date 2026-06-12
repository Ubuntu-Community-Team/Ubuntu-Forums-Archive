---
title: "xorg.conf in karmic"
date: 2010-01-23
forum: General Help
---

### Post by Narusegawa on 2010-01-23
Hi,

I've been trying to setup dual-screen in my system, but the control panel complains it can't find xorg.conf and so I can't save changes I make in the nvidia control panel. I was trying various methods of trying to get a dual screen working how I like it.

Left = 17" 1280x1024 that sometimes works (needs hitting a few times)
Right = 21" 1680x1050 main screen

I wanted to have everything on the right one, my main workspace. And I wanted a seperate x workspace on the left hand one. (Mainly so that when the one on the left decides to not work, I can use the panel thing at bottom to move apps to the right one)


 Now I know since 9.10 xorg.conf is non-existant and so determind on the fly or something.

Is there a way to get X to write out the current working xorg.conf that's it's using? i.e. It's auto determind x,y,z and that's what right now this second is being used. I want to save this as a working xorg.conf so I can fine tune it etc.

Thanks

---

### Post by ajgreeny on 2010-01-23
You can just get the system to produce a blank xorg.conf by running ```
gksudo gedit /etc/X11/xorg.conf
```Save the empty file that appears and there it will be waiting for your nvidia configuration changes to be added.  I do not have an nvidia card so can't tell you anything more about how to go about your further wishes.

By the way, if an xorg.conf exists, it is read and acted on, but as you say, there is not one by default, and often it is not needed any more.

---

