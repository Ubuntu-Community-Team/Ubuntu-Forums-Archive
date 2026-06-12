---
title: "How to disable nouveau to install Nvidia .run driver"
date: 2011-05-08
forum: General Help
---

### Post by neoargon on 2011-05-08
Since the driver in repository has a bug that freezes the display, I wish to install a previous version of the driver(which worked well in 10.10) downloaded from the nvidia website . But it seems that I need to disable nouveau driver before installing Nvidia driver 
How can I do that? please help 

I tried 
 ```
sudo apt-get --purge remove xserver-xorg-video-nouveau
```
but still nouveau is present .I don't know why 
Thanks in advance

---

