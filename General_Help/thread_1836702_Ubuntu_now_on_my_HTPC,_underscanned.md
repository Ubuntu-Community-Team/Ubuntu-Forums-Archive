---
title: "Ubuntu now on my HTPC, underscanned"
date: 2011-08-31
forum: General Help
---

### Post by btb36 on 2011-08-31
I'm gradually moving away from MS and dual booting the HTPC until the Ubuntu installation is finalised. I've already overcome a lot obstacles but one that I'm having trouble sorting is the under scan on the HDMI Panasonic plasma telly.

The graphics card is an ATI HD4800, and in windows its easy to drag the slider and set the image to match the screen size at 1080p resolution, and the picture is the correct size. Now in Ubuntu the image is slightly under scanned, the resolution is set to 1920:1080p @50hz in Monitor preferences, (though it's the only option there).

I should say I'm using the ATI hardware driver v11.8, as the built in driver over scanned by considerable margin (making it guesswork clicking out of sight to get  to applications, system etc), and the resolution was very poor, it was difficult to read text on standard webpage layout.

Is there a way to 'expand' the image to fill the screen as there is in Windows?

---

### Post by btb36 on 2011-09-01
I've fixed it now, edited the xorg.conf and made the scan size fit the screen.

---

