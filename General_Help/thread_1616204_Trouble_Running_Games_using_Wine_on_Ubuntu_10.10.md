---
title: "Trouble Running Games using Wine on Ubuntu 10.10"
date: 2010-11-07
forum: General Help
---

### Post by jeff_ on 2010-11-07
I'm having some trouble running the following games on Ubuntu 10.10 using wine:

Counter-strike source/Half Life 2
Warcraft 3/Frozen Throne

The games run, but very very slowly (unplayable). I managed to get Counter Strike 1.6 to work fine by setting the renderer to be 'Software' under the videos options, but the other games have no such option (that I'm aware of).

I'd never tried CSS or Half-Life 2 before with wine, but both worked fine in Windows and War3/FT worked before I upgraded Ubuntu to 10.10.

---

### Post by jeff_ on 2010-11-07
I get the following output in the console when running the frozen throne with -opengl

err:ole:CoCreateInstance apartment not initialised
err:winediag:X11DRV_WineGL_InitOpenglInfo The Mesa OpenGL driver is using software rendering, most likely your OpenGL drivers haven't been installed correctly
fixme:advapi:SetSecurityInfo stub
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 4 and card vendor 0000.
fixme:win:EnumDisplayDevicesW ((null),0,0x33f108,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5d4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f60c,0x00000000), stub!

---

