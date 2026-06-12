---
title: "Rotate Cube and Firefox Middle Click Conflict"
date: 2009-09-12
forum: General Help
---

### Post by hwttdz on 2009-09-12
I know that on one of my machines I have the rotate cube plugin mapped to the middle mouse button, and I also have firefox scrolling and opening a new tab attached to the middle mouse button. On one machine however when I am in a firefox window and middle mouse click instead of opening a new tab or scrolling I start rotating the cube.  Does anyone know how to resolve this conflict?  Thanks.

---

### Post by hwttdz on 2009-10-30
Bump.

Well the brute force way is to make a directory in your home and move all hidden files to that directory.  i.e. "mkdir hidden; ls -A|grep "\."|xargs mv -t hidden; mv hidden/* ." not exactly pretty, you'll lose all sorts of fun things such as firefox profile, thunderbird profile, any application preferences... but it does do the job.  You can of course steal files one by one back from the hidden directory.  So that makes matters better, not good, but better.

---

### Post by jelly5 on 2009-11-13
the way i get rid of that conflict is to disable the "Initiate" function under "Bindings" within the "Rotate Cube" section of the compiz menu and then make sure that the "Viewport Switcher" option is enabled on the main compiz menu. If you look in the settings for "Viewport Switcher" under the "Desktop-based Viewport switching" tab everything should be disabled except for "initiate plugin action" which should be set to "button 2" and the "plugin for initiate action" should be "rotate". If you do this you should be able to middle click to open new tabs in firefox, move icons around panels with middle click, autoscroll in firefox...etc. and use the middle button to rotate the cube. The only caveat is that to use the middle button to rotate you have to click directly on the desktop and not within any sort of window. This might not be what you want, but this is how i work around the conflict. Hope it helps!

---

### Post by elnetotaca on 2011-01-16
> **jelly5 said:**
> the way i get rid of that conflict is to disable the "Initiate" function under "Bindings" within the "Rotate Cube" section of the compiz menu and then make sure that the "Viewport Switcher" option is enabled on the main compiz menu. If you look in the settings for "Viewport Switcher" under the "Desktop-based Viewport switching" tab everything should be disabled except for "initiate plugin action" which should be set to "button 2" and the "plugin for initiate action" should be "rotate". If you do this you should be able to middle click to open new tabs in firefox, move icons around panels with middle click, autoscroll in firefox...etc. and use the middle button to rotate the cube. The only caveat is that to use the middle button to rotate you have to click directly on the desktop and not within any sort of window. This might not be what you want, but this is how i work around the conflict. Hope it helps!

Nice!!!!
worked for me, thanks for the info.

---

### Post by Jetro on 2012-11-07
> **jelly5 said:**
> the way i get rid of that conflict is to disable the "Initiate" function under "Bindings" within the "Rotate Cube" section of the compiz menu and then make sure that the "Viewport Switcher" option is enabled on the main compiz menu. If you look in the settings for "Viewport Switcher" under the "Desktop-based Viewport switching" tab everything should be disabled except for "initiate plugin action" which should be set to "button 2" and the "plugin for initiate action" should be "rotate". If you do this you should be able to middle click to open new tabs in firefox, move icons around panels with middle click, autoscroll in firefox...etc. and use the middle button to rotate the cube. The only caveat is that to use the middle button to rotate you have to click directly on the desktop and not within any sort of window. This might not be what you want, but this is how i work around the conflict. Hope it helps!
You. Are. Brilliant.

I apologise for this necrobump, but this person has to be thanked!

---

### Post by wildmanne39 on 2012-11-07
Old thread closed.

---

