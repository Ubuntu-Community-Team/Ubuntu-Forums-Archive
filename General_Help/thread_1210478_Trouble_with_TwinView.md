---
title: "Trouble with TwinView"
date: 2009-07-11
forum: General Help
---

### Post by dogbert55 on 2009-07-11
Well, I've had three problems while trying to use TwinView with Nvidia X Server Settings.

1) The "Make this the primary display for the x screen" box doesn't seem to work.  No matter which screen I select as primary, the panels stay on one of the monitors.  

2) The "Save to X Configuration File" button returns an error when I try to use it. The error is
 [COLOR="Red"]Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.[/COLOR]

3) Part of the screen I added gets cut off even though the correct resolution is selected.  When a window is maximized the minimize, maximize and close buttons are to the right, off the screen.  

I'm running Xubuntu 9.04 and have a Nvidia Quadro NVS 110M video card. Help with any of the three problems would be greatly appreciated.

---

### Post by earthpigg on 2009-07-11
you need to run it as root - the menu item doesn't give you that option. minor and confusing error on ubuntu's side of the fence.

> sudo nvidia-settings

you should be able to save your changes using that.

---

### Post by dogbert55 on 2009-07-11
Thanks, that was just what I needed.  Anyone with ideas on #3?

---

### Post by Finalfantasykid on 2009-07-11
This might be a long shot, but if you are using an analogue connection(VGA or whatever), then you might need to adjust the settings on your monitor since the screen might be outside of the bounders of your monitor.  The Monitor might even have an 'auto' feature which will do this for you.

---

### Post by dogbert55 on 2009-07-12
I figured out the final one.  I just adjusted the clock setting on the monitor all the way down.  I don't really screw with monitor adjustments all that much, so I didn't guess it would do that by the name.  Thanks for the help.

---

