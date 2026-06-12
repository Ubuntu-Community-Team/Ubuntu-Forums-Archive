---
title: "Can't find driver for graphic card (ubuntu 10.04)"
date: 2011-10-01
forum: General Help
---

### Post by munkefrugt on 2011-10-01
My screen Is full of red stripes, when i highlight it sometimes disappears, but I can't find a driver, tried with this guide. [http://superuser.com/questions/126630/what-graphic-card-drivers-to-install-in-ubuntu-10-04](http://superuser.com/questions/126630/what-graphic-card-drivers-to-install-in-ubuntu-10-04)

But got stock when I go to System => Administration => Hardware Drivers

Then it says: 

No proprietary drivers are in use in this system.

this is my graphic card by the way: 

martin@pepe-laptop:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M24 1P [Radeon Mobility X600] [1002:3150]

I hope someone knows how to make my screen pretty again. 
Thanks in advance:) And have a good day.

---

### Post by wanderingarticfox on 2011-10-01
I am not positive this will help; I use a ATI V4800 Workstation card and I run Gnome as my desk-top in Ubuntu. There are two reasons for this; 1] ATI is only writing Drivers for Gnome as far a the Proprietary Drivers For Linux are concerned and 2] using the additional drivers in System>Admin>Additional Drivers will get you the latest Ubuntu Tested drivers so you know they are stable.

I do not have the knowledge base at this time for downloading and installing the ATI Drivers directly and using them with Unity or KDE. I know people have done that but I can only tell you what worked for me at this time.

System>Admin.>Additional Drivers>activate the drivers listed. If no drivers are listed then check with ATI to see if your card is still supported.

---

### Post by 2F4U on 2011-10-01
Seems that you won't get proprietary drivers for your card since ATI doesn't support it:

[http://ubuntuforums.org/showthread.php?t=1351549](http://ubuntuforums.org/showthread.php?t=1351549)

---

### Post by wanderingarticfox on 2011-10-02
You can check here:

[http://www.amd.com/us/products/Pages/graphics.aspx](http://www.amd.com/us/products/Pages/graphics.aspx)

If it is not supported then I am afraid you are stuck with what you have. AMD/ATI dropped a lot of the older cards from Linux support. Use that link to make sure you get a card that is supported.

---

