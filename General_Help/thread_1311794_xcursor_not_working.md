---
title: "xcursor not working"
date: 2009-11-02
forum: General Help
---

### Post by &lt;NateTheGreat&gt; on 2009-11-02
When I try to change the cursor, I double click on the cursor I want and nothing happens. I tried clicking every button and nothing happens. With any of them. I can't run it in terminal cause when I type in "Xcursor" it says no such command. It isn't listed in the "known applications" when I press Alt-F2.

Not sure where to go from here...

---

### Post by usju on 2009-11-19
i am having the same issue...no fixes yet, i am using ubuntu 9.10 x64(ultimate 2.4). Namely if i click on a different cursor scheme in xcursor it has no effect. even after i restart system it does not get applied

---

### Post by Giblet5 on 2009-11-19
Are you using a GPU driver? Did you explicitly turn off the HWCursor option?

My device section looks like ```
Section "Device"
    Identifier     "NVIDIA Geforce 8800GTX"
    Driver         "nvidia"
    Option         "FlatPanelProperties" "Scaling=centered, Dithering=enabled"
    Option         "UseEDIDFreqs" "true"
    Option         "UseEDIDDpi" "true"
    Option         "AllowDDCCI" "true"
    Option         "DigitalVibrance" "12"
    Option         "RenderAccel" "true"
    Option         "AddARGBGLXVisuals" "true"
    Option         "HWCursor" "On"
    Option         "SWCursor" "Off"
    Option         "DPI" "96x96"
    Option         "AllowGLXWithComposite" "true"
    Option         "TripleBuffer" "true"
    Option         "EnablePageFlip" "true"
    Option         "ColorTiling" "true"
    Option         "EnableDepthMoves" "true"
    Option         "BackingStore" "true"
    Option         "DynamicClocks" "true"
EndSection
```

I don't expect to be able to use software cursors - I have them explicitly disabled, although that's the default anyway, I think...

---

