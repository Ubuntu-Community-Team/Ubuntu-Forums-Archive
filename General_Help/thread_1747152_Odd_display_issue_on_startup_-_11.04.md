---
title: "Odd display issue on startup - 11.04"
date: 2011-05-02
forum: General Help
---

### Post by bravo sierra echo on 2011-05-02
Mostly very happy with 11.04, apart from one niggle.

On starting up - before the login screen appears - I get a corrupted display of vertical white and black lines with some small corruption in the centre.

For the most part, it's a non-issue but it's really annoying when the computer chooses to do the regular filesystem check as I have to look at these horrible lines all the time it's working away!  They also appear while it's shutting down.

It happens on both Ubuntu and Kubuntu, I've tried a different monitor to eliminate that as a cause, and it's never happened before on any previous versions of Ubuntu (been using it every day since 2007).

I have a generic cheap graphics card, which has never given any problems before.

Has anyone else had this?

---

### Post by poodoopealeoaph on 2011-05-02
There have been a ton of issues with video cards in 11.04 all through testing. Basically, if you don't have an  Nvidia graphics card, it is a small miracle that you can even get any backlighting to even see the screen when you get to the desktop. So, I don't doubt that you are having some small issue with the video card because the new splash/boot screen is trying to grab an Nvidia card driver and it is conflicting...

---

### Post by poodoopealeoaph on 2011-05-02
If you det grub to run nomodeset every time you boot then you may be able to fix this. just hold shift while you are starting up and you'll be in the grum menu.

---

### Post by bravo sierra echo on 2011-05-02
That sounds plausible.

In that case, I wonder if it's possible to switch off the splash screen?

---

### Post by bravo sierra echo on 2011-05-02
Our last two posts crossed in the mail.

The nomodeset hint doesn't work, sadly.  Removing "splash" from the same line gives me a black screen, rather than the ugly black-and-white lines, but still doesn't allow me to read the text explaining that the filesystem check is happening.  It's an improvement though!

I think I'm just going to have to put up with this one.

---

### Post by tristan8276 on 2011-05-02
I have an old nvidia card.  My entire system is pretty old, so I wonder if I'm having a driver compatibility issue, but I digress... here's my issue:

I get the white vertical lines at boot too.  However, it will just hang at boot.  If I boot into recovery and choose 'restart X', it will boot to the desktop.  Unity fails every time, so I have to run in gnome classic.  Once I got a message about my video card (NVidia 5600XT) not being compatible with Unity...  so I thought going back to gnome classic would fix the issue.  However, I still have to boot X from recovery on every boot.  After playing with different boot options for several hours, I did get it to boot normally once by choosing 'reconfigure graphics' from the recovery menu.  

Also, if I choose anything from the gnome menu, it seems to take an inordinate amount of time to load now too.  The NVidia driver I'm using is version: 173

Thanks in advance,
Tristan

---

### Post by tristan8276 on 2011-05-03
Update:  After struggling with Unity and Gnome 3, I have reverted to a fresh install and I'm using the Ubuntu Classic desktop which seems to be working for me.  

It's definitely a driver issue though.  Somewhere there's a built-in nvidia driver that conflicts with the proprietary one from nvidia.  At least, that was the cause in my case.  When I'd go to "additional drivers" it would say my proprietary driver is active, but not in use.  If I removed the proprietary driver, it would fix the issue to an extent, but the video corruption would still take place.

---

