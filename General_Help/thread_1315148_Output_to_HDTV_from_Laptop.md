---
title: "Output to HDTV from Laptop"
date: 2009-11-05
forum: General Help
---

### Post by Kallahk on 2009-11-05
Hello everyone.

I recently bought an HDTV (Panasonic Viera TH-42PX80A) and have been trying to get my laptop, which is running Ubuntu 9.10 (was 9.04 yesterday, but nothing's changed since the update), to output nicely to it.

It almost works fine, except that the output to the TV is offset just slightly left and up. 

It's connected via a standard monitor cable from the external monitor output of the laptop.

During boot up as the output to the TV changes modes it looks fine for some parts. I think what I need to do is set te refresh rate to 70hz instead of 60 but in display properties it will only allow 60hz and it lists the TV as "unknown".

I did some googling and that brought me to looking at the xorg.conf. I've tried a bit, but I'm not entirely sure what I'm doing, and most of what google found is dealing with multiple GPUs and not laptops.

Here's my xorg.conf:
```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Virtual    1440 1668
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

```

Also, each time I enable the TV as an extra screen through display properties my Gnome panels seem to get placed randomly. Sometimes they stay where they are on the laptop screen, sometimes one or both jump to the TV.

So if anyone can help, t'would be grand, thanks!

---

### Post by kelvin.illa on 2009-11-05
I've also at my house a 32'' Panasonic Viera, and I'm using a MacBook 2,1 running 9.10. I've not yet touched xorg.conf. It's also labeled "Unknown" for me (which isn't really a problem).
[U]
For the screen offset:[/U] I'm assuming you connect via VGA (as opposed to HDMI).
- just go to the TV menu (while your computer screen is display on the TV), and find the settings to calibrate the H-pos and V-pos -- it should be there. I missed this one the first time I used connect mine to the TV.

What works (from experience):
- the computer must be connected to the external display before X starts for it to work properly -- what I do is log-out then log back in; you could also have the connection before you turn on the computer.

I don't know yet what more to add. Just ask away if you've questions.

---

### Post by Kallahk on 2009-11-05
Aha! I'd looked at the PC setup through the video menu, but not through the PC menu, so I've found it now and it looks grand!

Thanks very much!

One thing, though, there does seem to be a faint band of ever so slightly darker colour along the right hand side. It's not immediately noticeable, so i'm not too bothered. Any ideas what that could be?

---

### Post by kelvin.illa on 2009-11-09
[late reply]

I'm glad to be of service.

As for the dark coloration on the right hand side, I don't know; sorry.

---

