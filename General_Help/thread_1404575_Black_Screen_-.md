---
title: "Black Screen -"
date: 2010-02-11
forum: General Help
---

### Post by fdepinto on 2010-02-11
I'm trying to install Ubuntu 9.10 on a HP dv4-2170us laptop.  I get no video when trying the live CD, installing from CD, or running from USB flash drive.  The laptop currently runs Win7, but I'd like to set up a dual-boot.  I just can't get past the video problem - just a black screen.  Any suggestions?

---

### Post by jkovis on 2010-02-26
I have the HP dv4-2170us too and was getting the same black screen.  Following the advice below worked for me.  Also worth mentioning was that I first tried to install via USB but I couldn't safe graphics mode to work so I ended up burning a CD.

From [http://ubuntuforums.org/showthread.php?t=1413487]("http://ubuntuforums.org/showthread.php?p=8869071#post8869071"):

> **JiuJitsu500 said:**
> 
Anywho, at the language selector and live boot screen, press F4 I  believe (extra options one) and choose to boot into safe graphics mode.  The video card doesn't allow full acceleration until it's installed.  Once it is, install the proprietary driver and do all your updates, then  re-boot and all will be well.


---

### Post by fdepinto on 2010-03-01
> **jkovis said:**
> I have the HP dv4-2170us too and was getting the same black screen.  Following the advice below worked for me.  Also worth mentioning was that I first tried to install via USB but I couldn't safe graphics mode to work so I ended up burning a CD.

From [http://ubuntuforums.org/showthread.php?t=1413487]("http://ubuntuforums.org/showthread.php?p=8869071#post8869071"):

Thanks for the tip.  It worked great.

---

