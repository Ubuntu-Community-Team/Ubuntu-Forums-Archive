---
title: "No experience, No icons on desktop"
date: 2011-02-14
forum: General Help
---

### Post by supermaltese on 2011-02-14
So basically I have a ton of experience in the Windows environments and DOS dating back to 3.3 and Win 3.11 but I have no idea what I'm doing here.  I managed to get this installed alongside my Vista but Vista doesn't show up in the boot menu.  The problem I want help with for now, though, is after I log in, it goes to the pretty cool purple background and there's nothing else.  If I move my mouse cursor over to the left there does appear some black borders with white space inside.  I can click on them...The first one, on top, opens Firefox  So why don't I have icons? Do I need to install them?

---

### Post by jbiggs12 on 2011-02-14
If I'm not mistaken, the latest version of Ubuntu Netbook Remix actually doesn't have a desktop... you can access it through a file browser, though.

---

### Post by kerry_s on 2011-02-14
netbook requires 3d vid support, sounds like your not supported.
at the log in screen select "ubuntu desktop edition" in the session menu after clicking on your name. that should get you the standard desktop.

---

### Post by Krytarik on 2011-02-15
Like *kerry_s* said, the Netbook Edition depends on hardware-accelerated video support. If you don't have the correct driver installed, you can't barely see anything. The same is true for the effects in the Desktop Edition. The driver support is the same for both editions, you just have to find the driver which fits your video card/chip the best.

Starting with the build-in so-called driver jockey is generally a good idea:
Log into the Desktop Edition and go to "System -> Administration -> Additional Drivers". With that tool you can search for compatible drivers and install/activate them.

If you have an older ATI card/chip, which isn't supported by the proprietary drivers anymore, the Open Source Edge Drivers are currently the best solution:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers)
(look below that section to get to a list of now unsupported video cards/chips)

---

