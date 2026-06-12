---
title: "Dual screen problem with nvidia 11.10"
date: 2011-11-18
forum: General Help
---

### Post by ulugeyik on 2011-11-18
I have been happily running 11.04 with a dual-screen set up with Nvidia
Quadro NVS290 where I attach two VGA LCD screens through the DVI connector split into two cables. The screens are set to be next to each other and have different resolutions. when I have upgraded to 11.10 I ended up with an odd behaviour where my mouse goes between the two monitors without problems but if I drag a window from one monitor to another the window does not move from left to right monitor smoothly instead nothing happens until the mouse reaches the far right corner of the right monitor and the window shows up from that side. similar behaviour in the other direction too.

So looked around and I have found that nvidia may be the problem. One thing I noticed that the built in "Display settings" no  longer directs me to nvidia and I need to manually run "nvidia-settings" myself. In the first instance, there was an error which led me to try to upgrade to the latest drivers which did using the ppa:ubuntu-x-swat/x-updates . After some more fiddling around and activating the driver via "jockey-gtk", it worked until I rebooted the computer and it is now back to the same story.

Any suggestions on how to debug/fix this?


Thanks,

Turgut

---

### Post by ulugeyik on 2011-11-22
I have struggled with this for some more time but still no luck. Any pointers on how to debug it would be very much appreciated.

Thanks,

---

### Post by audiomick on 2011-11-22
you need to run "nvidia-settings" with root priviliges for it to be able to save back to the xorg.conf file. Don't know if this will fix everything, but it is certainly the case that things you change in nvidia-settings wont last past the next boot if you can't save back to the config file.

It is a graphical application, so start it using
```
gksudo nvidia-settings
```

---

### Post by ulugeyik on 2011-11-24
Hi,

Thanks but that does not solve the problem :<

---

