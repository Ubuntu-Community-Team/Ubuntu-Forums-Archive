---
title: "intel i3 graphics hd and etern screen on ubuntu"
date: 2010-09-15
forum: General Help
---

### Post by charlesbou on 2010-09-15
hi,
  I have a Vostro 3300 with a intel graphics hd. The laptop works  perfectly but when I try to use an external screen the image has like  vibration.  I don't really know how to discrib it. It's like it's the bad frequency.  But I try to change it without success...


  I try with windows and the second screen works fine.
  I also try to install a new kernel (2.6.43.6) it hasn't worked.


  As anyone an idea before I try to use the beta 10.10 ?
  Thanks.

---

### Post by smokeyd on 2010-10-01
I've got the same problem on my Toshiba laptop. 
Ubuntu Lucid 64bit installs fine, the normal laptop monitor works fine, but the external monitor doesn't. I have tried two different monitors, which both work fine on the same laptop when running windows 7. 
I have checked the resolution (1920x1080) and refresh rate (60Hz) in the docs of the monitor and they are selected in the system->preferences->monitor tool. When running the native resolution the screen vibrates like crazy, when it is running at 800x600 the virbation is not as bad, but it will still give you a headache.

I know the intel i915 driver is automatically detected by ubuntu and used (according to lsmod). lspci just shows me an VGA compatible Inter HD Graphics adapter, but no specifics on the type or model or anything like a number. The machine runs an intel core i3 processor with the integrated graphics chipset.
I am at a loss how to debug it further or find help.

---

### Post by mar_rud on 2010-10-02
Thread with same problem and some links to bug reports for this problem:
[http://ubuntuforums.org/showthread.php?p=9917435](http://ubuntuforums.org/showthread.php?p=9917435)

I've tried different resolutions/refresh rates without help. Unfortunately trying 10.10 beta from Live DVD (best way to check without installing) didn't help.

I have also Dell Vostro 3300 laptop with i3 and screen waves on Dell 2209wa LCD connected to VGA output. With Windows 7 there is no such problem. 

Latest i3 CPU's have new GMA HD graphic card (little different from 4500HD) and we need to wait for driver fix.

---

