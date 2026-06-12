---
title: "video card driver - nvidia-current or nvidia-173"
date: 2010-06-30
forum: General Help
---

### Post by de Bacon on 2010-06-30
I don't know how to determine which set of drivers to install for the new video card I just installed. When I use the function System/Administration/Hardware Drivers, it comes up with a choice of two with no way to know which is correct!  With my old card it showed three choices and none of them worked with that card, so now a new card but I don't want to go back to the old "no display" due to incompatible drivers. I don't know how to get out of that situation, been there too many times having to reinstall the OS.  This card seems to work okay just as is without the proprietary drivers loaded for simple function of a display.  How do I know which to choose, 
The script gives the choices:
Nvidia accelerated video graphics driver (version 173)
or
Nvidia accelerated video graphics driver (version current)(recommended)

Yet the first of the two is sort of automatically selected yet I don't know which is right with there being an option.  

I feel like an idiot, though the video card is the only real problem I have ever had with Ubuntu.  I finally (after 2 years) got a card that is said to work according to: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)

Thoughts would be appreciated, shared knowing would be better yet.  Thanks

---

### Post by jbrown96 on 2010-06-30
Nvidia-current.

---

### Post by him610 on 2010-06-30
> Yet the first of the two is sort of automatically selected yet I don't know which is right with there being an option. 
The top is probably highlighted because its the first one on the list. I also have an nVidia card. What you are seeing on the list are two versions of the same driver with the higher numbered version being the more recent version and it is also may provide better results.
Just highlight the version you want then click the Activate widget which will cause the selected driver to be downloaded and installed.

Have fun,

---

### Post by warfacegod on 2010-06-30
> 
Nvidia accelerated video graphics driver (version current)(recommended)

Recommended means just that. It's the one that Ubuntu developers are recommending you use for your video card.

---

### Post by de Bacon on 2010-07-01
>  I don't want to go back to the old "no display" due to incompatible drivers. I don't know how to get out of that situation, been there too many times, having to reinstall the OS.  

The logic of follow the logical choice failed me before, thus I ask now rather than taking on the assumption that all is known.  Thus I have yet to see any concrete answer based in supported evidence.  

I know a lot of you (probably most) know more about this stuff than I, too.  Yet to me, statements like go for it are kind of not very valid in my opinion.  I do believe that everyone is trying to be helpful too. 

Anyhow, sincere thanks,  

I shall see if more comes to view!

---

### Post by belize1334 on 2010-09-12
I run a pair of GeForce 7600 GT video cards in SLI mode. With the "current" version the screen was glitchy with strange color behaviors. Specifically, when panning between desktops the image would take a second or so to sync during which the colors were wrong. This was only with SLI enabled. If I disabled it the image was fine but I was wasting one of the cards. I switched back to v-173 and it immediately got better. I also got an improvement in FPS count playing Nexuiz. Oddly, it had the added benefit that the fans on the cards don't run as fast all of the time so the system is noticeably quieter while idling. 

My take... install the recommended driver first but if your system acts up then try one of the others.

---

