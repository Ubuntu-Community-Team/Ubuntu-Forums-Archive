---
title: "Nvidia splash screen"
date: 2006-02-22
forum: General Help
---

### Post by Fred Doolie on 2006-02-22
I installed the NVidia drivers and now my system has a graphic boot flash screen just like a certain other buggy OS.

Now, as long as I have a boot-up graphic, where is that file kept and how do I change it to something that I like?

---

### Post by nrwilk on 2006-02-22
I'm pretty sure that you cannot change it as you like.  It's directly embedded into the nvidia driver.  Though, I know you can suppress it from showing at all.

---

### Post by izmaelis on 2006-02-22
And to disable nVidia's splash screen you should set your xorg.conf:
```

Section "Device"
        Identifier      "Device[0]"
        Driver          "nvidia"
        BusID           "PCI:2:0:0"
        Option          "NoLogo"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
        screen 0
EndSection

```
where Option "NoLogo" is a line that you need.

---

### Post by annsachd on 2006-02-22
I like seeing that flash. I know I got the drivers installed correctly.

---

### Post by nrwilk on 2006-02-27
[QUOTE=annsachd]I like seeing that flash. I know I got the drivers installed correctly.[/QUOTE]
Me too.  Same reason.
Also, it's only about 1/4 a second long so it doesn't bother me.

---

### Post by Shikai on 2006-02-27
You'd have to restart X about...100 times before that splash would take as much of your time as editing your xorg.conf would take.

---

### Post by Nunu on 2007-07-25
Hi guys

I finally managed to get my duel heads to work, and noticed the sudden flash of what looks like  the Nvidia logo on startup. I know you can disable it, but is there any way to make it stay there for a couple more seconds instead of just a flash.\\:D/

---

### Post by DoktorSeven on 2007-07-25
Changing the logo:

> 
Option "LogoPath" "string"

Sets the path to the PNG file to be used as the logo splash screen at X startup. If the PNG file specified has a bKGD (background color) chunk, then the screen is cleared to the color it specifies. Otherwise, the screen is cleared to black. The logo file must be owned by root and must not be writable by a non-root group. Default: The built-in NVIDIA logo is used.


This should be put in the video card Device section of xorg.conf like the NoLogo option.

It doesn't exist for the older drivers; I assume this is something added when they changed the default splash to the black logo screen.

No way to lengthen the time it's displayed from what I can see, though.

---

### Post by Nunu on 2007-07-25
Thanks

It is a pity though. :(

It would be a cool idea for Nvidia to make the splash screen a configurable variable inside nvidia-settings... hint hint ;)

---

### Post by hebetude on 2008-02-03
Nvidia splash screen 2seconds

opening up nano and adding nologo 5seconds

All the time I save not watching lame *** proprietary commercials priceless

---

### Post by darrensnospam on 2008-04-14
On my xorg.conf, it already had the "NoLogo" "true" entry and I added it to the next device listed and I still get the nvidia splash screen.
If anyone has some other things I can try, I'd be very interested.
thanks.

---

### Post by crjackson on 2008-04-27
> **darrensnospam said:**
> On my xorg.conf, it already had the "NoLogo" "true" entry and I added it to the next device listed and I still get the nvidia splash screen.
If anyone has some other things I can try, I'd be very interested.
thanks.

I'd like to get rid of it too but adding the NoLogo option doesn't do anything on the latest drivers (at least on my machine)  I too feel like it should be an option in the nvidia-settings applet.

---

### Post by Chang An on 2008-05-03
I would also like to get rid of the logo.  It wasn't there till I started messing with the nvidia-settings to get tv-out working.  My Xorg also says "NoLogo" "True" but still shows the logo on boot.  I'm using Hardy.

---

