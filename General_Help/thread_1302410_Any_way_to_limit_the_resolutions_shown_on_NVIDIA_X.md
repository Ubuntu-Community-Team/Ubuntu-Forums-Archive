---
title: "Any way to limit the resolutions shown on NVIDIA X Server Settings?"
date: 2009-10-27
forum: General Help
---

### Post by Vietman on 2009-10-27
I generally only use 1024x640, 1152x720, 1280x800 and 1680x1050. I have my xorg.conf set up for custom modelines. But for some reason, the default resolutions besides those always show up. Can I suppress them? I only need those four, and the others are just cluttering up the selection.

Attached is my xorg.conf, if that helps.

(Also, on a side note, is there a way of selecting the default startup page on NVIDIA X Server Settings? It always goes to X Server Information, which is kinda useless. It would be better if it went to display configuration or color correction by default)

---

### Post by psycho5 on 2009-10-27
If your nvidia-settings works just fine, then you should let it be the default monitor resolution handler, then I think there's a box there that says "show only supported resolutions", atleast that was the case with my widescreen, it only shows the widescreen resolutions. I never bothered playing around with X. 

As far as masking the default resolutions, I have no clue. I don't think you should remove them, but I'm sure there is a file somewhere and you can edit it and mask them.

---

### Post by Vietman on 2009-10-27
> If your nvidia-settings works just fine, then you should let it be the default monitor resolution handler, then I think there's a box there that says "show only supported resolutions", atleast that was the case with my widescreen, it only shows the widescreen resolutions.

I don't have that option in Linux. It's something you can do in Windows, but that's beside the point. I have all these unusual and useless resolutions in the list that I would never dream of using.

---

