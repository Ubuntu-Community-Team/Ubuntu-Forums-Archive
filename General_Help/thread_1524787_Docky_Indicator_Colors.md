---
title: "Docky Indicator Colors?"
date: 2010-07-05
forum: General Help
---

### Post by Cam! on 2010-07-05
Is there a way through the Editor app (Gconf-editor) that I can change the color of the indicator lights on Docky? I'm using a light theme that matches the color of Radiance, but I'm unable to see the indicators.

---

### Post by archibald627 on 2011-01-17
open gconf-editor and go to /apps/docky-2/Docky/ThemeController:[B]

GlowTime = 10[/B] -- how long the urgent indicator glow animation is (in seconds), 0 to disable, -1 for infinite[B]

Theme = "Classic"[/B] -- this is the current Docky theme.[B]

UrgentHue = 150[/B] -- this is the value you can tweak to  change the color of the Urgent Indicator. This indicator is shown when  the window needs attention. The value can be from -180 to 180.

---

