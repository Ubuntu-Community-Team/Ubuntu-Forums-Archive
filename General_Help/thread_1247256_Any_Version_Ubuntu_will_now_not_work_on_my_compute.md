---
title: "Any Version Ubuntu will now not work on my computer!  HELP!!!"
date: 2009-08-22
forum: General Help
---

### Post by GregWI on 2009-08-22
I have a custom built computer using an ECS GeForce6100PM-M2 motherboard, AMD Athalon X2 64 5000+ processor,NVIDIA MCP61P chipset, 4GB Kingston DDR 5300 memory.

Previously, I downloaded and burned to CD working CDs of Ubuntu 7.10, 8.04 LTS, 8.10, 9.04 Previously, on other computers, I've had no problems with CDs earlier than 9.04. However, with this computer, 9.04 did something to the video that no version, not even 9.04 will work.

I first downloaded and burned 9.04.  I booted the computer using the 9.04 CD.  Everything worked great.  I was especially impressed with the desktop.  Then I shut down, unplugged the internal hard drive (Windows XP Pro SP3) and plugged in the external 40GB Maxtor hard drive to install Ubuntu 9.04.  Installation went very smooth.  Everything appeared normal, just as I installed many other Ubuntu systems.  I then rebooted using the Maxtor.  It rebooted well - mostly.  I got this goofy display in the upper left quadrant of the monitor (divide your monitor into 4 parts: the upper left, the upper right, the lower left and the lower right- all equal size) It was a brown desktop with a 3D Ubuntu image with no menus in the upper left quadrant of the monitor.  All the other three quadrants were just a black screen, and the mouse cursor would only display in the upper left quadrant.

I then disconnected the Maxtor and reconnected the internal drive and rebooted from the CD.  Now the CD displayed the same weird display!  So I then tried using the Ubuntu 8.04 LTS CD (that I also installed on many other systems) but that CD showed the same weird display!  Now, all my Ubuntu CDs when booting just from the CD have the same weird display with no menus.  So the only way I can shut down is by shutting off the power.

WHAT IS GOING ON!!!

Greg
:confused:

---

### Post by bootdoc on 2009-08-22
maybe something in the bios settings?  It sounds very strange.  I wish I could be of more help. I had some screen problems (not like yours) it turned out to be the monitor cable was nearly disconnected.

---

### Post by bootdoc on 2009-08-22
maybe something in the bios settings?  It sounds very strange.  I wish I could be of more help. I had some screen problems (not like yours) it turned out to be the monitor cable was nearly disconnected. 

You may try changing the boot options like nosplash and read the boot log as it goes by.

---

### Post by GregWI on 2009-08-23
:confused:Thank you bootdoc.  However, the boot is the same as it has been (I believe - I'll look at it again).  The system works great with Win XP Pro SP3 I have installed on the internal hard drive.  I'm wondering if it might be something in the video setting?  The BIOS/boot settings I am very familiar with, but do not know a lot about video settings, or just what Ubuntu may do now even when executed from CD.:confused:

---

### Post by P4man on 2009-08-23
does the bootsplash screen look normal, or weird as well?

Either way, there is nothing really that a live cd would do that would "stick". Its not gonna change bios settings, and it cant affect other cd's, so my guess is something happened when you switches drives. Loose cable, or maybe the videocard isnt seated properly ? Maybe the problem is even with your monitor? Does it have an 'auto" button, and if so, does that help?

---

### Post by GregWI on 2009-08-24
Thank you P4man.  When first loading Ubuntu, everything appears normal:  The Ubuntu screen with scrolling color bar underneath.  However, come to think of it, I'm not prompted for user-names or passwords. 

There is no video card.  The video is an integrated Nvidia. However, this is a different monitor.  This monitor is a Dell 19" HD widescreen flat panel with height adjustable stand.  I'm using the VGA.  To utilize the DVI, I'd have to get a video card with DVI.  However, my last system  had an AMD Athalon X2 64 with 2GB memory and a 17" Dell HD flat panel utilizing the DVI.  All Ubuntus worked fine then.  I had two hard drives with a dual boot bios where Windows was on one hard drive and Ubuntu 7.10 was on the other.  It worked great!

This does baffle me. 

Might it be that when loading Ubuntu, that somehow it modifies the video, though not to work properly?

---

### Post by P4man on 2009-08-24
a few things: the mostly black screen with the 3D ubuntu, im guessing is a garbled version of this?

[http://ubuntu-tutorials.com/wp-content/uploads/2009/03/ubuntu-jaunty.png](http://ubuntu-tutorials.com/wp-content/uploads/2009/03/ubuntu-jaunty.png)

when you see that, you could try just logging in, even if you cant see what you're typing, type in your username <enter> password <enter>

The gdm login screen may use a different resolution that the desktop, and is not shown during a liveCD, so.. doesnt hurt trying. If that works, we try solve that later.

Another thought is pressing the autoconfig button on your monitor. Thats in fact the only thing I can think off that might "stick". The monitor remembers a resolution and adjusts for it and saves that setting, though the timings might be off now. So press the "auto" button on the panel.

Last thought/ thing to try: if you press control alt F1 when you get to that garbled screen, does it give you a console ? Can you log in there ?

---

### Post by GregWI on 2009-08-24
Thanks p4man, I'll try those and let you know.

---

