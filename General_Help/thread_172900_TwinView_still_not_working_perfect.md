---
title: "TwinView still not working perfect"
date: 2006-05-09
forum: General Help
---

### Post by newpants2003 on 2006-05-09
thanx. i just fing the TwinView still not working perfect:
in physicl my two monitor looks like this:  one 15, one 19.

          |-------- |      
______|            | 
|        |            |
|        |            |
|_____|________|

but the system think the 15 one has more display area above. like this:


|----- |---------|      
|_____|             | 
|        |             |
|        |             |
|_____|________|

what can i do about?

---

### Post by Parkotron on 2006-05-09
Try this: [http://ubuntuforums.org/showthread.php?t=172058](http://ubuntuforums.org/showthread.php?t=172058)

---

### Post by newpants2003 on 2006-05-09
??
resolution on both screen is correct, it(i dont know what) think the smaller monitor has 15" monitor's width and 19" monitor's length.  the extra length * width doesnt display. icons and file i download to desktop always go into that area.
i hope you understand what im saying here.

---

### Post by Parkotron on 2006-05-09
That's very strange. What desktop environment (Gnome, KDE, XFCE) are you using? Does a maximised window fill the off screen space as well?

You could try shift the second screen vertically so that the region you mention would appear on screen, put you may then have an unusable area below the 15" monitor which wouldn't be much of an improvement. Can you switch the monitors with one another to make those icons visible?

[This]("http://www.ubuntuforums.org/gallery/showimage.php?i=1973&original=1&c=13") is a screenshot of my desktop. I can move my mouse into the black region, but KDE seems to be smart enough to never place anything in that region.

I'm sorry I can't be of more help.

---

### Post by newpants2003 on 2006-05-10
[QUOTE=Parkotron]That's very strange. What desktop environment (Gnome, KDE, XFCE) are you using? Does a maximised window fill the off screen space as well?

You could try shift the second screen vertically so that the region you mention would appear on screen, put you may then have an unusable area below the 15" monitor which wouldn't be much of an improvement. Can you switch the monitors with one another to make those icons visible?

[This]("http://www.ubuntuforums.org/gallery/showimage.php?i=1973&original=1&c=13") is a screenshot of my desktop. I can move my mouse into the black region, but KDE seems to be smart enough to never place anything in that region.

I'm sorry I can't be of more help.[/QUOTE]
im using gnome. the max window does not fill the off screen space.
maybe the best solution is buy another 19" monitor.

why linux makeing things so complicate compare with windows?

---

### Post by randomnote1 on 2006-05-11
did you want to view the same thing on both screens?  if so, the only way you can do that is to lower the resolution to one that works on both screens.  if you want to use a true dualing monitor setup you need to edit your xorg.conf file.  Here's my Device section.  The red part is my 19" monitor and the null is my TV.  That seems to be the best solution.

> Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 MX 420]"
    Driver         "nvidia"
    Option "TwinView" "true"
    Option "TwinViewOrientation" "RightOf"
    Option "TVOutFormat" "SVIDEO"
    Option "TVStandard" "NTSC-M"
    Option "SecondMonitorHorizSync" "30-50"
    Option "SecondMonitorVertRefresh" "60"
    Option "MetaModes" "1280x1024,1024x768;[COLOR="Red"]1280x1024,NULL[/COLOR];1024x768,1024x768;800x600,800x600;640x480,640x480"
EndSection

---

