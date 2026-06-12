---
title: "Saturated images on my Firefox"
date: 2011-04-07
forum: General Help
---

### Post by hektor_555 on 2011-04-07
Hi,
Firefox shows images saturated. When I look at the same sites on my Chromium they are totally fine. My Ubuntu is 10.10, Firefox is 4.0, and I have ATI drivers installed (as Ubuntu additional drivers). Could this drivers be messing up with Firefox? I've noticed in ATI Control Center Firefox is chosen as default browser, but it is the only possible choice. I attached a screenshot of My Firefox vs my Chromium in appearance. Could someone HELP ME PLEASE??? This is very annoying. Thanks!

---

### Post by lithopsian on 2011-04-07
Could well be related to hardware acceleration and so indirectly to your graphics drivers.  Try switching off hardware acceleration in the Firefox options.  Of course the difference might be due to hardware acceleration in Chrome!

---

### Post by hektor_555 on 2011-04-07
> **lithopsian said:**
> Could well be related to hardware acceleration and so indirectly to your graphics drivers.  Try switching off hardware acceleration in the Firefox options.  Of course the difference might be due to hardware acceleration in Chrome!

Thanks for your reply. I switched off hardware acceleration in firefox but sadly did not make any difference :(

---

### Post by lithopsian on 2011-04-07
Is this something that seems to have changed since 3.6?  3.5?  3.0?

Pull up about:config and see what the values are for gfx.color_management.mode, gfx.color_management.rendering_intent, and gfx.color_management.display_profile.

---

### Post by hektor_555 on 2011-04-07
> **lithopsian said:**
> Is this something that seems to have changed since 3.6?  3.5?  3.0?

Pull up about:config and see what the values are for gfx.color_management.mode, gfx.color_management.rendering_intent, and gfx.color_management.display_profile.

Thank you so much for your help. It was like this since 3.6. Didn't have this laptop yet for previous versions. This are the values:

gfx.color_management.mode: 2
gfx.color_management.rendering_intent: 0
gfx.color_management.display_profile: this value is blank

---

