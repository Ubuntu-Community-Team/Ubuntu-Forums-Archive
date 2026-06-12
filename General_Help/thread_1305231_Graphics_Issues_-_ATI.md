---
title: "Graphics Issues - ATI"
date: 2009-10-29
forum: General Help
---

### Post by dbo117 on 2009-10-29
Hi,
I just installed the newest (besides 9.10) distribution of Linux on my laptop on Monday.
Laptop specs:
Aspire 5050
Processor: [AMD]("http://www.notebookreview.com/default.asp?newsID=3609#") Turion64 MK - 38 ~2.2ghz
RAM : 2x 1 gig sticks
Hard Drive: 80 GB Hitachi 5400 RPM HD
Gaphics: ATI Radeon Xpress 1100 integrated graphics (64-256mb shared memory)
My goal was to get World of Warcraft to run, and I did but it was only running 1-5fps.  So I tried to install OpenGL (The ATI version) via the add/remove feature and after I installed that when I ran WoW it didn't look like Verticle Aliasing was working, all of the polygrams were skewed so I exited wow and my whole desktop was like that.  I turned off my system but when I now reboot I get a black screen with random horizontal stripes of color.  I am currently on a Live CD of Ubuntu 9.04.  What could I do to fix this problem short of a total reinstall?

Thanks

---

### Post by dummy910 on 2009-10-29
I would boot into **Recovery Mode** when you at your Grub selection screen. Once there a dos like menu should appear and 1st see if you can boot into your desktop from there, and make the needed changes(sudo gedit /etc/X11/xorg.conf), then reboot normally.

Here's my xorg.conf file, with the default ATI driver,  loading  glx, and all the eye candy, desktop-cube, GL Screensavers etc work(haven't loaded any heavy duty games yet)
> Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "ati"
EndSection


---

### Post by dbo117 on 2009-10-30
That didn't work :-| It tells me the display cannot be activated.  I can activate Terminal in Recovery Mode, but I can't get into Ubuntu through it.  What else could I try?

---

