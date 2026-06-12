---
title: "HELP WITH DELL Monitor"
date: 2010-02-02
forum: General Help
---

### Post by razbicu on 2010-02-02
I am a newbie to Linux.... Love it. BUT My screen resolution is not working with this monitor. I have 2 displays. My Main display is the Dell 23" wide-screen and my secondary display is just some generic brand 15" standard. the standard screen is is plugged via vga cable and the dell is plugged in via dvi. I am not sure why my resolution can only be set to 1152x864 (4:3). I know that this Dell ST2310 23" Full HD Widescreen Monitor is capable to have better resolution with Ubunutu...

Please help.... I know Linux can do it.... just don't know where

Here are Specs for the Dell:[B]
Panel Size:[/B] 
23"
**Aspect Ratio** 
Widescreen (16:9)[B]
Optimal Resolution:[/B] 
1920 x 1080 at 60Hz
**Contrast Ratio:** 
Dynamic Contrast Ratio 50000:1 (max)
**Response Time:** 
5ms
**Viewing Angle** 
(160 vertical / 160 horizontal)
**Color Support:** 
16.7 million colors
**Pixel Pitch:** 
0.266 m

---

### Post by howefield on 2010-02-02
What's the make/model of your graphics graphics card ?

---

### Post by razbicu on 2010-02-05
I have this:
ATI Technologies Inc.
Sapphire
Radeon X300/X500/X1050

And I have an AMD athlon 64bit 3200+ 2.01GHz
2 gb ram

---

### Post by Sylvester Ink on 2010-02-05
My best guess would be to create two "screen" entries in the xorg.conf file with the required settings per screen.  However, I've never had any experience with running two monitors on Linux, so I couldn't say for certain.  (I'll leave this question to the more experienced users . . .)

---

### Post by serpentracer on 2010-02-05
have you tried to use ati's drivers?  I seen them in the package manager before along with Nvidia's drivers.
I think it's the full set of ATI's catalyst suit.

---

### Post by razbicu on 2010-02-06
yes, I have all of them installed. still nothing.

---

### Post by Sylvester Ink on 2010-02-07
The problem is solved.  Ubuntu was reinstalled and the monitors were properly detected.

---

### Post by thecliff on 2010-02-07
Glad to read it is fixed.

The problem is that once ATI drivers are installed, you cannot tell which version of the driver you are using.  Therefore, there may be more up to date drivers that will fix problems you are having.

See "[A Beginner's Guide to ATI Drivers]("http://ubuntuforums.org/showthread.php?p=7996934")" in this thread.  This helped me with my 24" monitor when I could not use 1920x1200.  Basically uninstalled the ATI drivers and reinstalled the newest ATI proprietary drivers.

---

