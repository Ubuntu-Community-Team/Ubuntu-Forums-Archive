---
title: "Docked and undocked settings"
date: 2009-06-25
forum: General Help
---

### Post by cunawarit on 2009-06-25
I've never been a full time Ubuntu user, but I have come back to it recently. So be patient with me, I am not a GNU/Linux guru. 

I want to use it for image processing on the go on a little Dell Latitude D420 laptop, and I have GIMP, Raw Therapee, Qtpfsgui, and Flicker Uploader working well. This is great, this means it does everything I use my Windows XP desktop at home for... 

However, I've had a few issues:

Mouse speed with external mouse,totally unusable! Even at the slowest setting in:

System > Preferences > Mouse

Fixed it editing 10-x11-input.fdi with:

<match key="info.capabilities" contains="input.mouse">
<merge key="input.x11_options.AdaptiveDeceleration" type="string">7</merge>
</match>

7 is a good setting for me. And now the slowest setting is about right 

But it is annoying to have to then go to mouse settings again when you undock and want to use the trackpad instead.

The other problem that arose from docking was changes to xorg.conf to accommodate the higher resolution external display

Virtual res increased to:

SubSection "Display"

		#Virtual	2304 1058	 <--- this
		Virtual 2048 1050		<---- this fixes it

This caused the graphics effects to be turned off, but the above fixed it.

What can I do? Can I have multiple mouse speeds for different devices? But more importantly, is there a way to use the external monitor with higher resolution without it adding too high a resolution virtual display that kills the graphic effects?

PS: 9.04 does overall seem VERY nice!!! Quite fast and snappy even on this old slow laptop.

---

### Post by cunawarit on 2009-06-26
OK, shutdown and suspend scripts. That's where the key lies. I'll give it a go this weekend.

---

### Post by cunawarit on 2009-06-26
Or: [http://ubuntuforums.org/showthread.php?t=1076486](http://ubuntuforums.org/showthread.php?t=1076486)

---

