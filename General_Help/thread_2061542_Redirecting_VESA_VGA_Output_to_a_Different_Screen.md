---
title: "Redirecting VESA VGA Output to a Different Screen"
date: 2012-09-22
forum: General Help
---

### Post by JustYakov on 2012-09-22
So I have a laptop which, other than a broken graphics card, works fine. If I run Windows or Ubuntu Live CD with the 'nomodeset' option, which uses the vesa driver rather than the nvidia one, which causes a GPU lockup. It works fine, but only displays on the laptop screen, not on the external monitor which is connected to it.

Considering the fact that, on Windows, when redirecting the output to the monitor it does so with a refresh rate of 1Hz, can I redirect the VGA output to be only on the external monitor?

Thanks.

---

### Post by dcstar on 2012-09-22
> **JustYakov said:**
> So I have a laptop which, other than a broken graphics card, works fine. If I run Windows or Ubuntu Live CD with the 'nomodeset' option, which uses the vesa driver rather than the nvidia one, which causes a GPU lockup. It works fine, but only displays on the laptop screen, not on the external monitor which is connected to it.

Considering the fact that, on Windows, when redirecting the output to the monitor it does so with a refresh rate of 1Hz, can I redirect the VGA output to be only on the external monitor?

Thanks.

Considering that most laptops automatically send output to the external port when the lid is closed, then why not just do that?

Once Ubuntu gets to the login screen is is using the X system which can be configured by the various display tools or manually changing the xorg.conf file.

---

### Post by JustYakov on 2012-09-29
Sorry for the late reply.

> **dcstar said:**
> Considering that most laptops automatically send output to the external port when the lid is closed, then why not just do that?

I tried that, it doesn't display anything. In fact, the laptop display does not turn off when I close the lid.

> **dcstar said:**
> Once Ubuntu gets to the login screen is is using the X system which can be configured by the various display tools or manually changing the xorg.conf file.

Any suggestions on how to do that? Because every time I try `Xorg -configure`, it either complains that the X server is running (when lightdm is running) or that "the number of screens doesn't match the number of devices detected" (when lightdm is stopped).

---

### Post by JustYakov on 2012-09-29
Also, if it helps, xrandr display multiple settings, all with 0hz refresh rates, and using Ubuntu without X but with the nvidia driver (nouveau?) displays on both the laptop and external screens.

---

