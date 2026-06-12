---
title: "Please Help-Live CD Freeze Video Scrambled"
date: 2011-11-15
forum: General Help
---

### Post by flagbag on 2011-11-15
Although computer savvy, new to Ubuntu. Been trying to try it then install it for years, but seems it does not work on my computer.

I suspect it is the video card, mine is Nvidea GeForce 7800 GT and others have indicated problem with this card and Ubuntu. 

I thought patience would prevail and new version would take care of it, but alas--my disk for Ubuntu ver. 11.10 does not work either (I have been trying for about 4 years now with different versions).

Always I get a scrambled-looking screen, and the computer freezes... no mouse nor keyboard control. Screen looks like either of the two following pictures:
[IMG]http://a.yfrog.com/img611/205/suw7.jpg[/IMG]
or like this:
[IMG]http://a.yfrog.com/img875/9462/stns.jpg[/IMG]

I have seen some help in threads that are very old (like from 2007) or are worded in a way that is too complicated (like "install nvidea driver") that is too advanced for me without telling how to do that... 
   Please..  if anyone could please take time to set me on  the right track with HOW to install the driver, if that's what is needed, considering my system freezes after I select "Try Ubuntu without installing on computer."
  AMD Athlon 64 3500+
  32 Bit MSI Moboard
  3GB RAM
  Nvidea GeForce 7800 GT
  Also have XP SP3 on same system
Thank-You!

---

### Post by Quackers on 2011-11-15
Try the nomodeset boot option as described in the guide below.
(choose the live cd instructions)

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If that works you can install Ubuntu. On the first reboot of the new installation you should use the nomodeset boot option for the installed system as described later in that same link.
Once the new installation is booted you can then install the nvidia-current driver by clicking on Additional Drivers.

---

### Post by flagbag on 2011-11-15
Great... I will try that straight-away and report back.... Thanks!!

---

### Post by Quackers on 2011-11-15
Good luck :-)

---

