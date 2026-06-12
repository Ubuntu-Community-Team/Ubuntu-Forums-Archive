---
title: "Middle Mouse button emulation"
date: 2009-11-10
forum: General Help
---

### Post by natearn on 2009-11-10
I have been having this strange problem with my mouse when I log in. The middle mouse button emulation (mouse1 + mouse2 -> mouse3) is active for my logitech mx518 gaming mouse. The strange thing is that this feature will randomly correct itself after a while.

The mouse is a 6 button mouse with scroll wheel, so the middle mouse emulation shouldn't be on. After several attempts to disable this feature using a .fdi file (I'm not sure if I was writing it incorrectly or if it just wasn't working), I found that running this command:

xinput set-int-prop 7 227 8 0

seemed to disable the emulation. 7 being the mouse ID, and 227 being "Evdev Middle Button Emulation". This is, to me, more of a band-aid than a fix. Can anyone tell me what I should be doing to properly disable the emulation?

---

### Post by SKLP on 2009-11-28
> **natearn said:**
> I have been having this strange problem with my mouse when I log in. The middle mouse button emulation (mouse1 + mouse2 -> mouse3) is active for my logitech mx518 gaming mouse. The strange thing is that this feature will randomly correct itself after a while.X disables mouse button emulation as soon as it detects a click with one of the "additional" buttons (meaning not the left or right button). It really should not be done this way, a better way would be to disable it for all mice which have more buttons than two( as soon as they are detected ).

> **natearn said:**
> 
The mouse is a 6 button mouse with scroll wheel, so the middle mouse emulation shouldn't be on. After several attempts to disable this feature using a .fdi file (I'm not sure if I was writing it incorrectly or if it just wasn't working), I found that running this command:

xinput set-int-prop 7 227 8 0

seemed to disable the emulation. 7 being the mouse ID, and 227 being "Evdev Middle Button Emulation". This is, to me, more of a band-aid than a fix. Can anyone tell me what I should be doing to properly disable the emulation?

This fdi file seemed to do it for me:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="info.capabilities" contains="input.mouse">
   <merge key="input.x11_options.Emulate3Buttons" type="string">false</merge>
  </match>
 </device>
</deviceinfo>

```

Xorg will probably not use HAL in lucid, though. Which means this will have to be done in some other way.

---

