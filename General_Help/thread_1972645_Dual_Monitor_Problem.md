---
title: "Dual Monitor Problem"
date: 2012-05-03
forum: General Help
---

### Post by Rctfan on 2012-05-03
Hey, I have a problem with my dual monitor setup.  Whenever I try to unmirror the monitors and set them side by side, I get an error telling me that the requested position is outside the allowed limit.  I can place the the monitors over and under each other, but I can't put them side by side.  This problem only occurs when I use the AMD proprietary drivers.  Any one have any idea on how I can fix this?

---

### Post by cortman on 2012-05-03
Have you tried it with an xrandr command?

```
xrandr --ouput HDMI1 --left-of LVDS1
```

For instance, substituting your monitor arrangement for HDMI1 and LVDS1.

---

### Post by Rctfan on 2012-05-03
How do I know what to put for of HDMI1 and LVDS1?

---

### Post by QIII on 2012-05-03
Are you doing this through the Catalyst Control Center?

---

### Post by Rctfan on 2012-05-03
Oh, I feel stupid.  I have just been trying to use Ubuntu's display settings.  I didn't even think of the catalyst control center.  It works now.  Thanks guys!

---

