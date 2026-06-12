---
title: "comandline shows at Boot"
date: 2010-06-07
forum: General Help
---

### Post by drascus on 2010-06-07
I was fiddling with my boot up trying to get things faster here is what I changed.

I edited /etc/default/grub 

first I did this because I read profiling my boot would get me better speeds
GRUB_CMDLINE_LINUX_DEFAULT="quite splash profile"

then I did this I read that nomodeset was better for my Nvidia card
GRUB_CMDLINE_LINUX_DEFAULT="quite splash nomodeset"

Long story short now when I boot I get all this comand line junk at the beginning and then my splash screen. Is there any way to correct this and just get my splash screen at boot? also this has slowed down my boot.

---

