---
title: "[NOT SOLVED] Unable to start the settings manager 'gnome-settings-daemon'"
date: 2012-07-11
forum: General Help
---

### Post by landstander on 2012-07-11
Here it is, 2012 and this problem is back with a Vengeance on Ubuntu Natty.
**Note:** None of the solutions posted in this thread:
[_"Unable to start the settings manager 'gnome-settings-daemon'"_]("http://ubuntuforums.org/showthread.php?t=955679")
currently work to solve this problem in Ubuntu Natty.[B]

My setup[/B]:
&#65279;Distro: Ubuntu 11.04 64bit
Codename: Natty Narwhal
Desktop: Gnome (unsure which version, whichever one runs by default if selected at login from a default Unity installation)
CPU: Intel Quad Core 2 Extreme, X9650, 64Bit, (3GHz per core)
GPU: GeForce 8800 GT
GPU MEM: 512 MB
GPU MEM Interface: 256 MB
GPU VBIOS: 62.92.24.00.00
MoBo: Asus (Can't remember which one and too lazy to look it up)
MoBo MEM: 4GB

**Here is how I reproduced the problem**:
Step 1.) Installed grandr 0.4.1 also known as "Display Geometry Switcher" was added to the panel by right clicking on the gnome panel
Stpe 2.) Installed all the Ubuntustudio packages from the synaptic package manager.
Step 3.) Installed the compiz fuzion window manager along with its icon and selected "Grid" from the window management section under its settings.
Step 4.) My monitor can be rotated for long document editing and media production, so the "Display Geometry Switcher" was opened up and the screen was rotated to the left for work in that orientation.
**Note:** This is the point where the Display Switcher should have put up a message asking me if my settings looked ok, with an automatic timer counting down to switch the display back to normal if I didn't select ok within the given amount of time. This window was never displayed, the screen was rotated to the left as was selected but it never asked me if it was ok. This is also the point where my customized theme and icon combination quit working.
Step 5.) Used the Display Geometry Switcher to rotate back to the normal view. (Again it didn't ask if this was ok like it normally does, it just did it).
Step 6.) I attempted to get my customised theme and icons back and this is where the dreaded message that has no solution appears.

**Error message (as if you haven't seen this enough already):**
> 
Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with DBus, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.


**Current Actions:**
Completely uninstalling Unity and Compiz to see if that does anything. I don't need unity since I use the gnome desktop anyway.

**Questions:**
1.) What is wrong, why am I getting this error message, and how do I fix it?
2.) How can the computer regain control of themes and the desktop look and feel plus icon sets?
3.) If there is no answer to the above two questions then, are there any Linux distributions that come with a dark theme by default straight out of the box? (I have intermittent migraine/eye problems and having to work with dark text on a white background is painful, and working with light text on a dark background solves this problem for me).

Thanks for any help or insights you might have on this problem.

---

### Post by robtygart on 2012-07-11
Check out your "System Monitor" and look to see if there is anything running. Looking for "settings manager" I would guess, from the error report.


There is Always Kubuntu, and it has a lot of themes, plus more you can download.

---

