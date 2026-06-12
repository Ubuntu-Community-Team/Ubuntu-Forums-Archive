---
title: "How do you get xubuntu to boot with the glint video driver instead of vesa?"
date: 2010-06-13
forum: General Help
---

### Post by mfernandez on 2010-06-13
Does anyone know how I can get xubuntu to boot up using the glint video driver instead of vesa?  I am trying to get it loaded on an older machine and a previous version of ubuntu worked using the glint driver but the latest version of xubuntu (10.04) is using the vesa driver.  Which is not working for me.  I have tried ubuntu, xubuntu and lubuntu all version 10.04 and neither of them has worked.  They all boot up into a terminal window (no GUI).  
 
I tried creating an xorg.conf file and added a line specifying the glint driver.  After doing that and trying to startxfce4 I get an error saying that it cannot load the glint module.  Unfortunately that machine has no internet connection either.  I guess it hasn't recognized my wireless card either.
 
Any help would be greatly appreciated.

---

### Post by mfernandez on 2010-06-14
Anyone?
 
I am assuming that the glint driver is included/installed by default.  Maybe this is not the case.  Can anyone tell me how to install the glint driver if that is required?

---

### Post by mfernandez on 2010-06-16
I finally got xubuntu running on this old machine (live, not installed  yet).  I did not specify any boot options.  I let it boot up as normal  into the terminal.  Then I installed the glint video driver that I  downloaded from another machine (copied it to this one via usb drive)  using dpkg.  Then I had to create an /etc/X11/xorg.conf file to specify  using the glint driver, busid and also a few other things.  Then I  entered startxfce4 and viola, here I am.

So far I like the desktop but it is still a little slow.  I assume I  would pick up some speed by actually installing (versus the live version  I am running from cd).  I think I will play around with this for a few  days and then maybe try lubuntu.

Finally!!!!!

---

