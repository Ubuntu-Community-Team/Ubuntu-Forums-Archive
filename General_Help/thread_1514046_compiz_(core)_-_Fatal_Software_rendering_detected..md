---
title: "compiz (core) - Fatal: Software rendering detected."
date: 2010-06-20
forum: General Help
---

### Post by Ta2dNerd on 2010-06-20
Try to start compiz and I get this:

compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager


OpenGL works everywhere else.  Started happening after upgrading to lucid.  Uninstalled and reinstalled compiz packages, tried different Nvidia drivers, and no luck.  Any ideas?

---

### Post by Ta2dNerd on 2010-06-20
Anyone?  Anyone?  Bueller?  Bueller?

---

### Post by Ta2dNerd on 2010-06-20
Oh, the huge manatee!!!!  !](*,)

---

### Post by Ta2dNerd on 2010-06-21
Bumping again...Anyone know about this issue????

---

### Post by Ta2dNerd on 2010-06-21
compiz-check script output:

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G73 [GeForce Go 7600] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

---

### Post by dwel on 2010-06-22
I hate to see someone with a problem go this long with no help, but, have you tried the [COLOR="Blue"][compiz forums]("http://forum.compiz.org/")[/COLOR]?

---

### Post by joseielpi on 2011-05-18
I have the exact same problem (among many, many, others) It's being months, searched everywhere, no solution. I guess that's the way things go with lucid. You loose one feature after the other... then spend whole days trying to fix things, then give up. In my humble opinion, Lucid is a major step backwards from hardy.

---

### Post by wildmanne39 on 2011-05-18
> **joseielpi said:**
> I have the exact same problem (among many, many, others) It's being months, searched everywhere, no solution. I guess that's the way things go with lucid. You loose one feature after the other... then spend whole days trying to fix things, then give up. In my humble opinion, Lucid is a major step backwards from hardy.
Hi, I would like to help you if I can what video card do you have?

---

### Post by joseielpi on 2011-05-20
Hello there!

    this is what terminal says:

     CODE

    [00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)]

    I appreciate your disposition to help!:D

---

### Post by linuxinstalledfromhdd on 2011-05-20
I don't have a solution for it. I do have a suggestion. Try creating a Ubuntu 10.10 bootable USB stick, and boot your computer from that. See if you can get test it out, and see if that doesn't solve your issue with something more recent than Lucid.

---

### Post by joseielpi on 2011-05-22
Thanks, I'll give it a try as soon as I can. I am very willing to quit on Lucid, although it's a LTS version, I haven't being able to find a solution to it's multiple problems.

---

### Post by joseielpi on 2011-05-24
Hello again. Your suggestion did not work, the problem remained. However, looking at this very forum i did stumble upon this:

 [URL="https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#How%20It%20Works"]

  I'm guessing it has something to do with the desktop effects and other graphic failures. As soon as i test it, i'll tell you.

---

### Post by mikejonesey on 2012-02-18
should anyone find this thread in the future; this error can be caused by having installed the incorrect open gl libary (install a different one)...

---

### Post by dwel on 2012-02-19
Nice!!!

---

