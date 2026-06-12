---
title: "use ID_FS_LABEL_SAFE in nautilus mounter"
date: 2009-11-12
forum: General Help
---

### Post by fantomduck on 2009-11-12
Hi everybody,

I'm using the ubuntu 9.10 desktop distro. i'm trying to access automatically from the cli a USB drive. the problem i face is that when the gnome automounter detects the USB disk it mounts it based on its label. if the label has spaces (FreeAgent Drive) and try to access the device from a command including $DEV (to get its name), the $DEV brings only the first part of the mount name (FreeAgent) and so the drive path is not correct. 
i searched a lot and found out that i could use this one: [http://superuser.com/questions/53978/ubuntu-automatically-mount-external-drives-to-media-label-on-boot-without-a-us](http://superuser.com/questions/53978/ubuntu-automatically-mount-external-drives-to-media-label-on-boot-without-a-us) .
the problem is that nautilus automounter is grabbing the device and the rule i created is not taking part on the mounting procedure. then i thought that i could overcome all errors if i could tell to automounter to mount the drive not with ID_FS_LABEL_ENC rule but with ID_FS_LABEL_SAFE so that it will put an "_" on each space of the name of the device. i searched a lot but i couldn't find anywhere a howto explaining how i can ask from nautilus to use  the ID_FS_LABEL_SAFE whenever a USB disk is plugged in.

the solution with the UUID labeling is not a solution for me since i want to use it for any device i may plug in the USB.

thanks in advance,

E.D

---

