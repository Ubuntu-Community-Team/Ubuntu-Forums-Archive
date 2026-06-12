---
title: "2d vs. 3d"
date: 2012-06-12
forum: General Help
---

### Post by ddjolley on 2012-06-12
I just purchased a Shuttle model XS36V and installed Ubuntu 12.04.  When I log in, I am able to select between 2d and 3d.   I select 3d.   However, after the session is initiated, $DESKTOP_SESSION reveals that I am actually running in 2d.    First, it would seem to me that I would not be presented with selection options if 3d was not available.  Is that the case?  If so, why am I winding up in 2d?  I realize that Ubuntu 3d doesn't work with vintage video hardware.  However, it  would be a bit of a surprise for me to learn that it doesn't pretty much work across the board with new hardware currently being sold.  So, basically, I am trying to figure out where I stand.  Do I need to return this thing or what?  Thanks for any input.

             ... doug

---

### Post by PhantomTurtle on 2012-06-12
You might not have the proprietary graphics card drivers for your graphics card installed. To install them, open the dash and search for "Additional Drivers" and open it. There, install the driver that is listed by clicking Activate. Restart and select 3d. This should boot into Unity 3D and have full 3D acceleration.

---

### Post by ddjolley on 2012-06-12
When I search for additional drivers, I am told that no proprietary drivers are in use on this system.  Good thought though.  Thanks for the input.

            ... doug

---

### Post by PhantomTurtle on 2012-06-13
I found a thread about this: [http://ubuntuforums.org/showthread.php?t=1969640]("http://ubuntuforums.org/showthread.php?t=1969640"). Post 4 says,
> Just for information - I've just purchased a Shuttle XS36V and getting results for display resolution of 1024 x 768 or 800 x 600 so anyone thinking of buying this shuttle will not get the full graphics capability. I'm running Lubuntu 12.04LTS and tried with Ubuntu 12.04LTS both give same results.
Note:The XS35V uses the Mobility Radeon HD7410M graphics which is the same animal as the XS36V apart from graphics - by the looks of things. 

This means that you will most likely not be able to use Unity3D, because there is no Linux driver for it([http://superuser.com/questions/422288/linux-support-for-intel-gma-3650]("http://superuser.com/questions/422288/linux-support-for-intel-gma-3650")). I would try Gnome Classic, XFCE or LXDE as an alternative since I have found Unity2D to be a bit buggy.

---

