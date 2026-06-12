---
title: "Display required to boot Xubuntu 9.10?"
date: 2009-11-27
forum: General Help
---

### Post by jonszy on 2009-11-27
I have a box running Xubuntu (9.10) that I ssh into over my wireless network.   In some rare cases, I hook up a keyboard, monitor and mouse to it in order to do some debugging of some custom software I have running on it.  However, these are typically not attached.

I've noticed that it doesn't complete the startup sequence until I plug a display in.  Once I turn the machine on, I can wait some inordinate amount of time, and can tell that it isn't starting up since it does not connect to my wireless network.  (I have it configured to do so) Another clue here is that the wireless card lights up once the interface is initialized (also done after startup).

If I plug a display in, I see that it is still at the boot splash screen.  It then immediately continues to start up, brining up the network interface I need to connect to the box remotely.

Why must a monitor be detected in order to complete this boot sequence?  Can anyone clue me in on any configuration files that might control this behavior?

Thanks.

---

