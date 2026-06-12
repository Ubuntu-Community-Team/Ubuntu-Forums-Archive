---
title: "Firefox fonts turned ugly after changing Amarok appearence via KDE SytemSettings"
date: 2010-07-07
forum: General Help
---

### Post by isaac wilson on 2010-07-07
I use the latest Ubuntu release (10.04 LTS Lucid Lynx) with gnome, I'm pretty new to all things linux and have found many answers on this forum. I need some help on this new problem... I followed the instructions to change Amarok's colors here:[ http://ubuntuforums.org/showthread.php?t=1318289]("http://ubuntuforums.org/showthread.php?t=1318289")

Now something weird happened during that and now Firefox (3.6.3) fonts are all jaggy and terrible for reading, which is really distressing me... I tried the solutions from google's results for "firefox fonts ugly ubuntu" and similar solutions suggest adding a font package... I have done that... and nothing changes... I have undid the settings using the instructions in the link, restarted things, and no progress... Can anyone help me figure out how the KDE settings mess up firefox, and how to revert the mistake?

---

### Post by IronDoctorChris on 2010-07-12
I had the same problem. I'm not entirely sure how I fixed it but I think it was because I went back into the KDE appearance settings and changed the anti-aliasing and DPI settings.
IIRC I enabled AA and increased DPI to 120 in the KDE menu. Then increased DPI in the gnome appearance settings. Then decreased in gnome again, then reset the KDE font settings to default. HTH; sorry I couldn't tell you exactly what fixed it for me.
Good luck

---

### Post by aticodejon on 2010-10-15
It also happened to me, and I fixed it by:

1)reinstalling systemsettings (through synaptic, no need to reinstall kdebase-workspace-bin).
2)In Systemsettings, go to Appearance->Fonts
3)select 'Enabled' in Use anti-aliasing dialogue
4)click on Configure
5)select 'Use sub-pixel rendering'
6)choose RGB
7)choose 'Slight' in Hinting Style dialogue
8)click Ok.

Then I did a full reboot (not sure if it's needed, but just in case).

This is assuming your gnome settings are the same (Appearance->Fonts->Details under Linux Mint 9), if not, just choose the corresponding options.

Hope that helps :)

---

### Post by veko on 2010-10-22
I've had this same problem in Karmic and got it again in Maverick after testing KDE.

This solution worked for me: [http://ubuntuforums.org/showthread.php?t=1362214](http://ubuntuforums.org/showthread.php?t=1362214)

Basically I just edited the contents of  $HOME/.fonts as shown in the link.

But there is something badly wrong in KDE, since it messes up font settings so badly.

---

