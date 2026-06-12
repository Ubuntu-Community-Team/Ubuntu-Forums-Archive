---
title: "Anti-aliasing/smoothing - disabling"
date: 2006-02-12
forum: General Help
---

### Post by grav on 2006-02-12
Not only the fonts but every single pixel in my Gnome-desktop is antialias'ed.
How can I disable this?

---

### Post by dcstar on 2006-02-12
[QUOTE=grav]Not only the fonts but every single pixel in my Gnome-desktop is antialias'ed.
How can I disable this?[/QUOTE]
There is no such thing as non-font "aliasing", if things look that wrong on a LCD screen then you need to let it "Auto adjust" to the particular resolution/refresh rate that you are using.

If it is on a CRT, then you may be using inappropriate settings that the monitor cannot handle.

---

### Post by mcduck on 2006-02-12
If it's a flat screen, you should find out it's native resolution and set Gnome to use that. Flat screens aren't very good with different resolutions as everything smaller/bigger than secreens native resolution has to be scaled and that can make the picture look fuzzy..

---

### Post by grav on 2006-02-13
[QUOTE=mcduck]If it's a flat screen, you should find out it's native resolution and set Gnome to use that. Flat screens aren't very good with different resolutions as everything smaller/bigger than secreens native resolution has to be scaled and that can make the picture look fuzzy..[/QUOTE]
It's a laptop computer with an LCD screen (Acer TravelMate 660)
It can go up to 1400x1050 in Windows, is that its native resolution then?
How about color depth, does that matter?
And do I change screen resolution -  in Gnome, or in the XWindows config. files?

---

### Post by mcduck on 2006-02-13
You'll have to find the resolution from your laptops manuals (or google). Most likely it's not 1400x1050 but something a bit smaller. Native resolution is not the  max resolution, it's the resolution that the display was built to.

CRT displays can change their resolution with no problems as pixels are created by sweeping electron ray. Change the speed the ray moves, and you'll get different resolution. TFT's are different, as pixels are built to the display, so you can't really change the resolution, you'll have to scale everything to fit the built-in resolution instead.

You'll want to edit /etc/X11/xorg.conf as that is what tells Gnome what resolutions you have available. So find the correct display resolution, and edit the modelines to give you that resolution (and some others, you might want, altough they won't be as sharpmas using the native resolution). For example I have set HorizSync 30-69 and VertRefresh 50-100, as they are the values I fond from my monitors manual. Then I added a line 'Modes       "1152x864" "1024x768" "800x600" "640x480"' under subsection 'Display' (In Section 'Screen' near the end of the file). The first resolution will be the default, and the rest are choosable with Gnome's Screen Resolution dialog.

edit: I did some research with Google, and I suppose the native resolution for TravelMate 660's screen is 1024x768. I'm not absolutely sure about that, as many sites only report the max resolution of 1400x1050 and I didn't find any specs from Acer's web site..

---

