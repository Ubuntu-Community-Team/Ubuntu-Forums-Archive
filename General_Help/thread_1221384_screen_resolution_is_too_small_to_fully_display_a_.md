---
title: "screen resolution is too small to fully display a dialog window.  Fix???"
date: 2009-07-23
forum: General Help
---

### Post by audiomason on 2009-07-23
I have a very small lcd screen (800x600) and many dialog windows are too large to fit, causing the confirmation buttons to get cut off.  Some dialogs are resizeable, but many are not.  Is there a fix for this?  

I remember once seeing a feature that let you set the screen resolution higher and scroll the screen.  Does anyone know how to do this?

I used to be able to force this screen into a higher resolution (1024x768) with an older kernel, but not anymore... :confused:

Thanks for the help!

---

### Post by ohzopants on 2009-07-24
I don't know how to do what you're trying to do.

As a temporary workaround you can always hold down the alt key and click and drag anywhere in the window to move it so that all the buttons are visible. Note that this works terribly if you have compiz' snap to edges enabled, it works okay with gnome's though.

---

### Post by audiomason on 2009-07-24
> hold down the alt key and click and drag anywhere in the window to move it so that all the buttons are visible
Thanks Ohzo, that's a good trick to know!

---

### Post by Glich on 2009-07-24
Ye, I have this problem as well. Some dialogue boxes have their OK or cancel buttons just underneath a panel. You can put buttons on the panel to hide the panel. This sometimes works. I'd be interested to know the answer to you problem.

---

### Post by ohzopants on 2009-07-24
You're very welcome.  That's one of the little things that I've gotten used to in gnome that make using windows even harder. (Always on Top, Edge snapping, and taskbar rearranging are just a few others)

---

### Post by CatKiller on 2009-07-24
> **audiomason said:**
>  I remember once seeing a feature that let you set the screen resolution higher and scroll the screen.  Does anyone know how to do this?

I believe that this is done by setting a Virtual resolution. I've never used it, so I can't tell you the specifics, but it might help you search for a solution.

In case it helps, this is what man xorg.conf says about the Virtual setting for the Display Section.

```
       **Virtual**  _xdim_ _ydim_
              This optional entry specifies the virtual screen  resolution  to
              be  used.   _xdim_  must  be a multiple of either 8 or 16 for most
              drivers, and a multiple of 32 when running in  monochrome  mode.
              The  given  value  will be rounded down if this is not the case.
              Video modes which are too large for the specified  virtual  size
              will  be  rejected.   If  this entry is not present, the virtual
              screen resolution will be set to accommodate all the valid video
              modes  given in the **Modes** entry.  Some drivers/hardware combina&#8208;
              tions do not support virtual screens.  Refer to the  appropriate
              driver-specific documentation for details.

       **ViewPort**  _x0_ _y0_
              This  optional  entry  sets the upper left corner of the initial
              display.  This is only relevant when the virtual screen  resolu&#8208;
              tion is different from the resolution of the initial video mode.
              If this entry is not given, then the  initial  display  will  be
              centered in the virtual display area.
```
Another thing that might help you in the meantime is that you can press hotkeys to emulate clicking on the buttons that you can't see. Alt-A is generally Apply, Alt-C is generally close. If you can get to see the buttons sometimes, but don't want to have to drag the window around every time, the hotkey is Alt and whichever letter is underlined.

---

### Post by SecretCode on 2009-07-24
> **ohzopants said:**
> As a temporary workaround you can always hold down the alt key and click and drag anywhere in the window to move it so that all the buttons are visible. Note that this works terribly if you have compiz' snap to edges enabled, it works okay with gnome's though.

As a workaround to the workaround, if you hold Shift as well as Alt that toggles the snap to edges behaviour.

---

