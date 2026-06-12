---
title: "Xubuntu in Vbox using quite a lot of ram"
date: 2012-02-17
forum: General Help
---

### Post by mastablasta on 2012-02-17
This is my first vbox install. i noticed i have a free 20GB partition so i decided to dedicate 8GB fo it to Xubuntu.
 
I installed it just fine. I gave it 512MB ram (of 2GB) and 128MB graphics (host mashcine has a single core GPU). i installed guest additions, however i am not sure if i installed the proprietary graphics driver or not. anyway i am running it full screen. works relatively ok with a reasonable speed. however it is just not that snappy as i would expect it to be.
 
I checked the RAM usage and noticed it is using 374-380 MB ram. is that normal? is that ok? to me that seems quite a lot for XFCE. or is it just reading it wrong since it is running in vbox?

---

### Post by Toz on 2012-02-17
> i installed guest additions, however i am not sure if i installed the proprietary graphics driver or not
You won't be able to install the proprietary graphics driver in a vm - it will run the VBOX video driver instead. 

> works relatively ok with a reasonable speed. however it is just not that snappy as i would expect it to be.
I find that mine runs as expected (my main laptop is dedicated to Xubuntu 11.10) and the speeds seem comparable for most stuff. Heavy graphical processing apps/games run much better on a dedicated system though (as opposed to in a VM).

> I checked the RAM usage and noticed it is using 374-380 MB ram. is that normal? is that ok? to me that seems quite a lot for XFCE. or is it just reading it wrong since it is running in vbox? Running xubuntu 11.10 in VBox on this system now. Similar type setup except I've allocated 768MB ram.
```

free -m
             total       used       free     shared    buffers     cached
Mem:           749        632        116          0         37        278
-/+ buffers/cache:        [COLOR="Red"]317[/COLOR]        431
Swap:         1021         22        999

```
...With firefox open, 4 tabs, and a couple of terminal windows, 317MB in use.

Are you running 32 or 64-bit? There is another thread around here somewhere where someone has noticed that 64-bit consumes more memory - which kind of makes sense (64-bit vs 32-bit memory addresses).

---

### Post by snowpine on 2012-02-17
Reported RAM usage will vary from computer to computer (and from day to day depending on your tasks). You may find this page amusing/informative:

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

In my experience 512mb is adequate for the 'Buntu family, as long as you don't push it too hard (excessive multitasking, etc). 1gb or more is better.

---

### Post by mastablasta on 2012-02-17
aha! free m shows 140MB, so i guess that is the correct value then. was actualyl expecting to be closer to 100MB. need to turn off more compositing then. 

show 318 under used in that mem line. nothing running (appart forom terminal and the usually stuff).

i was just comparing it to Chrunch bang (which uses older verison of XFCE and also X i believe) and that one has 80 MB on the laptop propper install.

this is great way for safe websurfing BTW. :-) and i think a better option than wubi at least in my case when i want to check something to give support to others or learn a bit about the OS.

---

### Post by snowpine on 2012-02-17
Xubuntu is nothing more or less than Ubuntu with the Xfce desktop environment. It is not designed to be "lightweight" in the same way as Puppy, SliTaz, TinyCore, etc. except by virtue of the fact that Xfce uses less resources than Unity.

I would argue that the exact RAM usage number is irrelevant; the fact that one OS uses 140mb and another uses 80mb will not impact your enjoyment of the distro. (RAM is a resource meant to be used; so long as the number doesn't approach 100% and you don't use swap, there is no impact on performance.)

Personally my favorite in the .deb family is CrunchBang (disclosure: I am a moderator on #! forums) as I've found it to be faster and more stable than anything in the Buntu family. (Although about a year ago I made the switch to .rpm.)

---

