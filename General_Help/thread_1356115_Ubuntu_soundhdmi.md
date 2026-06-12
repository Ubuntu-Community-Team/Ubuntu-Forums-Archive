---
title: "Ubuntu sound/hdmi"
date: 2009-12-15
forum: General Help
---

### Post by Albertint on 2009-12-15
This is sort of a two sided problem, so let me begin first with what I have:
*36" Dynex television (supports all Xorg settings perfectly)
*Dell Inspiron 1525 (Which is a decent laptop with HDMI output)
*Ubuntu 9.10, which by the way ROX (With it's improved intel gma support)

So I installed it and it works perfectly, however, I'm in a bind because when I leave the HDMI plugged in and reset the computer, the image overscans the screen.

So I think, "Fine, I'll just plug in the HDMI after I've setup the computer!", and that helps, but with the fact I can't get any HDMI sound ouput unless I reset the computer, which leads back to the overscan problem.

And on top of that, the Xorg.conf file is clear (blank, no text or settings) so I'm actually having a 3-sided problem.

Any suggestions?

---

### Post by Albertint on 2009-12-16
Also, might I add that my attempts at getting xorg.conf to work have failed. Whatever that part of the trick is that people use to reset x.

Unless I'm just doing it wrong.

---

### Post by Albertint on 2009-12-17
Is this just a hard question or did I word in a way that no one would understand? All I need help with really is how to inform Xorg that I have a 720p tv hooked up and how NOT to have the image going outside the screen (Gnome toolbar are cut off, youtube videos in fullscreen are hard to view entirely). I dunno if this answers anyones apparent confusion over the op, but OH WELL!

(P.S.: Like I said, this problem only occurs when I restart the system. I can turn the computer on then hook it up to the TV, but that results in no sound going through HDMI. Yes, I know you have to set it through the sound control panel. I did that, and nothing.

---

### Post by Albertint on 2009-12-25
Eh, screw it. I'm using VGA now.

---

### Post by thyraios on 2009-12-26
you can try to change the settings in Display Preferences: uncheck mirror screens, set the correct resolutions for each screen and reboot (I also had problems with resolution over HDMI when the TV was connected at boot). About sound over HDMI I couldn't find another solution other that booting with the TV connected

---

### Post by NFblaze on 2009-12-26
Hey dude, the Xorg stuff has always been confusing to me (especially since nowadays it's automatically setup for most monitors), and I have not set up a dual monitors before nor am Im rich enough to have an HDMI tele or HDMI output port. Though, according to the web here is some references for you to look at if you still want to try to use HDMI.



[X/Config/HDMI]("https://wiki.ubuntu.com/X/Config/HDMI")

and

[X Configuration]("https://wiki.ubuntu.com/X/Config")

Good luck. If successful, please post your steps or what you did to resolve for a future user. Good luck.

---

