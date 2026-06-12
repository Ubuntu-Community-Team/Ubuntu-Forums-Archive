---
title: "Very odd scrolling mouse pointer problem-Acer 3810T"
date: 2009-09-01
forum: General Help
---

### Post by markw10 on 2009-09-01
I just installed Ubuntu 9.04 64 Bit on my Acer Aspire Timeline 3810T-6415.  This machine has 4GB and 500GB of hard drive space.
The only accessory I have on it is a Logitech Trackman Wheel Trackball.
The computer came with Vista but after reformatting I installed Ubuntu.  After connecting to WiFi Update Manager quickly launched and had a list of updates.  What is odd is if I hold my mouse pointer over the right up/down scroll bar the scroll bar starts moving down.  I'm not pressing any buttons on the trackball at that time or even moving it.
Also, I opened up OpenOffice Calc and had a very similar problem.  As soon as I put the mouse pointer over the actual cells within OpenOffice the cells started scrolling but not vertically, they scrolled from left to right.  It does not stop.  Again, I'm not pressing any buttons or moving the trackball. 
I thought it may be an issue with my Logitech Trackman but I unplugged it and rebooted and have the same issue when I use the computer's trackpad.  Also, I don't think it's the trackpad because I tried turning the trackpad off while having the Logitech Trackman plugged in.  None of this changed anything.
I didn't use Vista that long but didn't see this issue. Could this be a setting in the BIOS?  I'm using 1.10.  Could it be some type of hardware problem?  
What I did notice, when I selected Install Updates on the Update Manager I got the following error message:
"Could not grab your mouse.  A malicious client may be eavesdropping on your session or you may have just clicked a menu or some application just decided to get focus.  Try again"
All I can select is Close and try again but again, I have not been able to get beyond this point.  Any idea what is causing this?

---

### Post by P4man on 2009-09-01
sounds like a "feature" of your touchpad. Maybe this helps to turn it off:

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by markw10 on 2009-09-02
Thanks for the response.  Unfortunately that didn't seem to fix it though.  I do hope this is some type of bug or just something that isn't supported since this is such new hardware and that maybe is fixed in the next release.  I even tried both OpenSUSE and Mandriva with KDE 4.2 on both and had a similar issue and some other additional issues so I almost think it may be something linux kernel related at this stage of the kernel.  I don't really think it is a hardware problem.

---

### Post by P4man on 2009-09-02
when i googled your problem, I found a few similar threads related to windows, giving the same problem before installing a driver, so I think it somehow is hardware related. You could be right though, it may need a new driver. Perhaps open a bug report on launchpad?

---

### Post by markw10 on 2009-09-03
Thanks.  I'll give that a try.  it will be nice when this is resolved.

---

