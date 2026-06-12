---
title: "installing video driver help"
date: 2011-11-18
forum: General Help
---

### Post by davidtheo on 2011-11-18
I am trying to install an new video driver NVIDIA-Linux-x86-285.05.09.run
it is in my download dir. eg home/userdir/downloads

The file has the following permissions -rw-rw-r--

When I run the command 
```
sudo service lightdm stop 
```
I just get a black screen
when  I run sudo sh name_of_file.run in that screen nothing happens

do I need to move the driver I need to install into an other folder.

can you please tell me step by step what I need to do.

Thanks

---

### Post by efflandt on 2011-11-18
Why not install it as a package like everything else in Ubuntu?  I believe that once you add the x-swat source, installing nvidia-current package should install the most recent nvidia drivers (currently 285.05.09).

[http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

---

### Post by davidtheo on 2011-11-18
> **efflandt said:**
> Why not install it as a package like everything else in Ubuntu?  I believe that once you add the x-swat source, installing nvidia-current package should install the most recent nvidia drivers (currently 285.05.09).

[http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

I downloaded the updates but that still did not give me the driver of my video card, maybe I need to install Ubuntu 10.XX for the drivers

---

### Post by davidtheo on 2011-11-19
> **efflandt said:**
> Why not install it as a package like everything else in Ubuntu?  I believe that once you add the x-swat source, installing nvidia-current package should install the most recent nvidia drivers (currently 285.05.09).

[http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

Thanks fflandt after some more playing around with it I have got the second monitor displaying.

I just can not move windows on to it right now.

Thanks for your help :)

---

