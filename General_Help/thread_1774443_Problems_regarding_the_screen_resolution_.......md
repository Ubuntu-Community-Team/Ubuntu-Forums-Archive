---
title: "Problems regarding the screen resolution ......"
date: 2011-06-03
forum: General Help
---

### Post by infinitybot on 2011-06-03
Hi Guys , :p
I run Ubuntu 11.04 :popcorn:
My LCD Monitor supports a resolution of 1600x900
All thing ran fine until :-
Today I switched on my Ubuntu Box
My resolution always changes to 1024 x 768
The Monitors Application shows the Max resolution as 1024 x 768 , I cant get above it. My monitor is listed unknown...
Whenever I edit my xorg.conf , the file goes missing after every reboot (See the screen shot)
PLEASE HELP! :(:(

---

### Post by Spr0k3t on 2011-06-03
Interesting, the /etc/X11/xorg.conf file vanishes on reboot?  Let's see if there's any info on the hardware that might help.

```
sudo apt-get install hwinfo
sudo hwinfo --display
sudo hwinfo --framebuffer
sudo hwinfo --monitor
```

Also, can you give us a little information your hardware?

---

