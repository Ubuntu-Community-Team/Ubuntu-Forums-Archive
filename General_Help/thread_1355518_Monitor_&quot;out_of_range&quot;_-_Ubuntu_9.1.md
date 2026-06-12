---
title: "Monitor &quot;out of range&quot; - Ubuntu 9.1"
date: 2009-12-15
forum: General Help
---

### Post by kwanseum on 2009-12-15
Hi, I'm running Ubuntu 9.1 and when as I login as me (adminstrator) the monitor is: out of range.  However, I can still login as the other users of the system.  In addition I installed Ubuntu a few days ago and logged without a problem between before now.

My computer is new but the monitor is very old.  The monitor refresh rate in this user (not admin) is 50 Hz but I seem to remember that in my account the refresh rate was about 60 Hz.  Could it be that the monitor does not function at 60 Hz and if so how do I change it under my login?  Also it said that the monitor is '*unknown*'.  

Furthermore, when I go to > system > preferences > display it says that my "*graphics card does not support the extensions for this tool" *and it gives me the option to* "use the graphics driver the vendor's tool instead*".  I'm not sure how that is relevant but just thought I'd mention it.

---

### Post by andy506 on 2009-12-15
I get that vendor tool warning come up when I have the nvidia video card drivers installed.  The app it suggests running has never been much good for me when setting refresh rates....screen resolution on the other hand works well.

Look for a file called xorg.conf inside /home/username.  It's probably hidden so include a period at the front of the filename.   You can set your monitor refresh rates in that file.    Might want to use the same file inside the working /home/working_username directory as a template.

---

### Post by kwanseum on 2009-12-30
> **andy506 said:**
> Look for a file called xorg.conf inside /home/username.

You can set your monitor refresh rates in that file.    Might want to use the same file inside the working /home/working_username directory as a template.

The only place I can find the xorg.conf file is in the folder:
/etc/X11

The contents for the file are:
```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
```

Perhaps I'm missing the point, but how does this file help me?

Thanks, Kwanseum

---

