---
title: "Compiz Rendering VLC Fullscreen Video, Cannot Control Playback."
date: 2011-02-28
forum: General Help
---

### Post by satyanash on 2011-02-28
Hi,
I have Compiz Config Settings Manager installed on my Ubuntu 10.04 machine.
All the effects are working properly and everything is running fine.
However when i play video with VLC Media Player, i would only get audio and no video. After looking this up i changed the output to X11 vidoe Output. I started getting video and audio.
But when i switch to fullscreen mode the fullscreen video window is rendered by Compiz and thus has all of those window effects like wobbly, minimize, maximize and stuff are also applied to the full screen video. It also does not have all those controls that vlc normally shows when you wiggle your mouse in full-screen mode.
I tried disabling the Video Playback option from the CCSM window, but to no avail.
The same thing also happens for the full screen view of Google Chrome.
And the only way to leave full screen is to press F11 again. In this case the tab stacking area which drops down doesn't appear at all, also the exit full screen option which too drops down also does not appear.
It seems Compiz is blocking all of those interactive buttons like the floating control panel in VLC and Tab stacking area in Chrome.

Help Please it's a bit annoying.:popcorn:
Satyajeet

---

### Post by satyanash on 2011-03-02
bump.

---

### Post by vikramk.ibs on 2011-09-30
hi

I faced same problem.

After some experiments, here I am with the solution

You must be having CCSM, 
Check option Composite and check on the option 'Unredirect fullscreen windows'

Restart

Enjoy!

:guitar:

PM me if you are still facing problem, will try to answer

---

### Post by satyanash on 2011-10-01
Thanks, for the reply. However i think this problem was fixed in an update. The problem automatically stopped occurring. Anyway i no longer use compiz. I switched to Xmonad and Fvwm. 
Thanks Again!
:popcorn:

---

