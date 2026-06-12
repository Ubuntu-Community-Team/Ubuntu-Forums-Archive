---
title: "Visual Effects not enabled. Got an ERROR in compiz-check."
date: 2010-01-31
forum: General Help
---

### Post by asn_knight on 2010-01-31
Well, I couldnot enable desktop effects in my comp and accordong to the Desktop Effects FAQ I ran the compiz-check the terminal window showed like this :

```
 Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Mobility Radeon HD 3650
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use
```So How do I make it right?!

Thanks.

---

### Post by lidex on 2010-01-31
Can you post the output of these terminal commands:
```
cat /etc/X11/xorg.conf
cat /var/log/Xorg.0.log | grep EE
LIBGL_DEBUG=verbose glxinfo | grep error
```

That error "appears" to refer to dual or external monitors. Are you using more than one or external?
Also what driver version are you using? Output of this command:
```
uname -a
```

---

### Post by lidex on 2010-01-31
Have a look here:
[http://ubuntuforums.org/showthread.php?t=1159910]("http://ubuntuforums.org/showthread.php?t=1159910")

Follow the link in the last post.

---

### Post by asn_knight on 2010-01-31
Thanks a lot for the link. Will try it soon.
For now I went to System>Administration>Hardware Drivers 
and it showed 
ATI/AMD Proprietary FGLRX Driver 
is not activated.
and im downloadin and installing it.
 I ll let u know the outputs and also try the manual in the link after it~
Anyway Thanks a lot!

---

### Post by asn_knight on 2010-01-31
Dude, It worked!!!!
Thanks a ton! 
If u still want the outputs I can give you! ( I know that it ll be modified now after all the crap i have done :D)
Enjoy,
--asn_knight--

---

### Post by asn_knight on 2010-02-01
Dude, The visual effects is working just fine.
But my battery backup has suffered.
In Windows it comes to around 2 hrs and a bit more ( with aero and all effects)
while in Ubuntu its 1 hr 20 min with 'normal' visual effects(not even extra).
with extra it shows around 50 min or so!
Have any sol for that?

Thanks
--an_knight--

---

