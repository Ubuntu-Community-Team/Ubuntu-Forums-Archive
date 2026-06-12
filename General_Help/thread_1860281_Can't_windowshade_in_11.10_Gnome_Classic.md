---
title: "Can't windowshade in 11.10 Gnome Classic"
date: 2011-10-14
forum: General Help
---

### Post by haydentech on 2011-10-14
One feature which I use quite extensively is using the mouse wheel to shade/unshade a window.  In 11.04, this worked fine.  After upgrade to 11.10, I can't get it to work in gnome-wm or compiz.  When I try it with gnome-wm absolutely nothing happens, despite the windowshade setting being activated in ubuntu-tweak.  When I try it with compiz, it appears to work (the window rolls up) but then the window disappears, leaving only a shadow of the unrolled window on screen.  The only way to get it back to click on the window in the taskbar.  After that point, the window will never shade again.

Does anyone have windowshade working in 11.10 Oneiric?  I'd prefer a compiz solution, but I'll take any solution at this point, because I use this feature about 100 times a day.

---

### Post by antijen on 2011-10-15
I'm having the same issue in 11.10 with the unity desktop.

---

### Post by bitpicker on 2011-10-15
I second all of that. I want window shades... Yesterday I iconized a window in Unity (Skype), and it disappeared for good (probably an unrelated bug, it does not happen with other programs). No way to restore it, it appears. I prefer shading unused windows.

---

### Post by watgrad on 2011-10-15
> **haydentech said:**
> One feature which I use quite extensively is using the mouse wheel to shade/unshade a window.  In 11.04, this worked fine.  After upgrade to 11.10, I can't get it to work in gnome-wm or compiz.  When I try it with gnome-wm absolutely nothing happens, despite the windowshade setting being activated in ubuntu-tweak.  When I try it with compiz, it appears to work (the window rolls up) but then the window disappears, leaving only a shadow of the unrolled window on screen.  The only way to get it back to click on the window in the taskbar.  After that point, the window will never shade again.

Does anyone have windowshade working in 11.10 Oneiric?  I'd prefer a compiz solution, but I'll take any solution at this point, because I use this feature about 100 times a day.

Yes I also have this problem. Though I am experiencing the same problems in 11.10 Unity. Shade works fine on my updated (11.10) laptop.  But on my desktop I have the exact same problem you mentioned.  How does one go about trouble-shooting this? 
My laptop was an upgrade from 11.04.  My desktop was a fresh install...

---

### Post by watgrad on 2011-10-15
Ok - what fixed this for me:
Open Software Sources
Enable Canonical Partners (both options) in the Other Software tab.
Also enable Pre-release updates and Unsupported updates in the Updates tab.
Close Software sources.
Perform an update with Update Manager.
(My computer installed a number of updates for compiz as well as the printing system)
After a reboot the window shade is working again.

Hopefully, the system will be more stable now as I experienced many crashed from compiz before this update - will keep you posted as the the stability with these releases...

---

### Post by CurlySurmudgeon on 2011-10-16
Thanks for the help.

I, too, had that problem.  Your instructions returned shading to a limited degree however now I'm left with white borders where the window will open when double-clicked.

Works but is aesthetically displeasing.

---

### Post by haydentech on 2011-10-17
I tried turning on the proposed updates, and downloaded the bleeding-edge compiz.  However, it actually made my problem worse.  Now compiz won't start at all, and I'm stuck with the lame metacity, which of course won't windowshade either.

On a related note, does anyone know how to set Gnome Classic to load compiz at startup in lieu of metacity?

---

### Post by glennric on 2011-10-18
haydentech:  Are you sure that you are actually running the GNOME Classic session?  I thought I was but it turned out I was not.  From a terminal type "echo $DESKTOP_SESSION" and see what it returns.  If it returns "gnome-fallback" then you are actually running the GNOME Classic (No effects) session.

What is happening is that the GNOME Classic session is failing, and the fallback is the gnome-fallback session (which is the GNOME Classic (No effects) session).  The reason it is failing is not because of compiz, but because of the notify-osd application failing to start.

If the above returns gnome-fallback then try editing /usr/share/gnome-session/sessions/classic-gnome.session and changing the line that reads
"RequiredProviders=windowmanager;notifications;"
to
"RequiredProviders=windowmanager;".
Then see if compiz starts.

---

### Post by unc0nn3ct3d on 2011-10-19
Ran all of the updates and they didn't fix a damn thing for me.  GAH! When will the nightmare that is 11.10 ever end?

> **watgrad said:**
> Ok - what fixed this for me:
Open Software Sources
Enable Canonical Partners (both options) in the Other Software tab.
Also enable Pre-release updates and Unsupported updates in the Updates tab.
Close Software sources.
Perform an update with Update Manager.
(My computer installed a number of updates for compiz as well as the printing system)
After a reboot the window shade is working again.

Hopefully, the system will be more stable now as I experienced many crashed from compiz before this update - will keep you posted as the the stability with these releases...

---

### Post by Granny_Geek on 2011-11-04
> **haydentech said:**
> One feature which I use quite extensively is using the mouse wheel to shade/unshade a window.  In 11.04, this worked fine.  After upgrade to 11.10, I can't get it to work in gnome-wm or compiz.  When I try it with gnome-wm absolutely nothing happens, despite the windowshade setting being activated in ubuntu-tweak.  When I try it with compiz, it appears to work (the window rolls up) but then the window disappears, leaving only a shadow of the unrolled window on screen.  The only way to get it back to click on the window in the taskbar.  After that point, the window will never shade again.

Does anyone have windowshade working in 11.10 Oneiric?  I'd prefer a compiz solution, but I'll take any solution at this point, because I use this feature about 100 times a day.
I've been searching for a solution to shading windows in Ubuntu 11.10 because I use it extensively as well, I used gnome tweak tool, then set the window setting to Toggle Shade instead of Shade, you will see a transparent outline of the window that is shaded but you will be able to work on the window underneath it, I guess that will suffice for now. Another difference in Ubuntu 11.10:-)

---

### Post by bitpicker on 2011-11-27
A recent update seems to have solved the problem, shading now works again as intended after being set in gnome-tweak.

---

