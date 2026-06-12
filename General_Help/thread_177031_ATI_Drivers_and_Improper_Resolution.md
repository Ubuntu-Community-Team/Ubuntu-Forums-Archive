---
title: "ATI Drivers and Improper Resolution"
date: 2006-05-15
forum: General Help
---

### Post by Zeno50 on 2006-05-15
Hi, I have Ubuntu Breezy Badger installed on my Acer Aspire 2020 laptop.

[LIST]
[*]ATI Mobility Radeon 9700 128MB
[*]1280x800 Resolution (widescreen)
[*]1.8GHz Centrino chipset
[/LIST]

I ran the X.org configuration utility. 
```
sudo dpkg-reconfigure xserver.org
```

And everything looked fine...I could use the correct resolution and everything.
Then I downloaded the xorg-driver-fglrx drivers for ATI.
Then I ran ```
sudo fglrxconfig
```
After going through the configuration for that I rebooted.  My 3D acceleration was working, but the only resolutions I could choose from were 1024x768, 800x600, and 640x480.  Which is not the correct one for my laptop, and isn't widescreen.

I tried redoing the x.org configuration for fglrx to no avail.  I also started from scratch removing the ATI drivers and configuring them again.  During the ATI configuration it asks which resolutions you'd like to choose and mine isn't listed.  Also I chose some other ones just to see and the only ones I can use (regardless of what I chose) are 1024x768, 800x600, and 640x480.  The ATI driver always gets my 3D acceleration working but doesn't let me choose the correct resolution.

Also I have a generic logitech optical mouse with a scroll wheel.  And after running the configuration my scroll wheel doesn't work.

Does anyone know what I can do?

---

### Post by z_diver on 2006-05-15
I have a 1280x800 display on my laptop also.  In /etc/X11/xorg.conf under Section "Screen" I have only 1280x800 listed for 24 bit resolution.  In fact, all color depths list just that one resolution which I think is safe since it's a laptop and the monitor is a known quantity.  So I'd recommend editing that file as root and then restarting X after you are done.

While in there, check your mouse configuration.  Something like this should allow you to use the scroll wheel.  ZAxixMapping is the important part. ```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

```

---

### Post by Zeno50 on 2006-05-16
Ok, so how do I edit that file as root (sorry, new to linux and not sure where I'm supposed to enter the password)? And by restarting X do you mean running the configuration again?

Also, if I don't mess with the fglrx ATI stuff I can use my correct resolution.  Is there any way to tell fglrx that it needs to use 1280x800?

---

### Post by Zeno50 on 2006-05-16
Nevermind, I figured it all out!  Thanks for the help!

---

### Post by Minosha on 2006-05-21
How did you get it to work, Zeno?

---

