---
title: "Subpixel smoothing causes text to be colourful"
date: 2010-06-09
forum: General Help
---

### Post by trotur on 2010-06-09
Hi!

I just bought a new monitor, Acer H243HX 24" 1920x1080. I have Ubuntu 10.04 and subpixel smoothing enabled with slight hinting and RGB-order (monitor has same RGB-order).

The problem is that fonts seems to have "too heavy" smoothing: **fonts doesn't look black but colourful. Text has almost unnoticeable but very irritating colour glow.** I have tried grayscale smoothing but with it fonts don't look as nice as with subpixel smoothing.

I have been wondering whether problem is associated with software or hardware. **Could problem be caused by the fairly large pixel pitch (pixel size) of my monitor (0.276 mm)?** I have used two other monitors with Ubuntu 10.04 and same smoothing settings. They had pixel pitch of 0.26 mm. I haven't noticed any colour glow in these monitors even though I have tried to see it.

---

### Post by dcstar on 2010-06-09
> **trotur said:**
> Hi!

I just bought a new monitor, Acer H243HX 24" 1920x1080. I have Ubuntu 10.04 and subpixel smoothing enabled with slight hinting and RGB-order (monitor has same RGB-order).

The problem is that fonts seems to have "too heavy" smoothing: **fonts doesn't look black but colourful. Text has almost unnoticeable but very irritating colour glow.** I have tried grayscale smoothing but with it fonts don't look as nice as with subpixel smoothing.

I have been wondering whether problem is associated with software or hardware. **Could problem be caused by the fairly large pixel pitch (pixel size) of my monitor (0.276 mm)?** I have used two other monitors with Ubuntu 10.04 and same smoothing settings. They had pixel pitch of 0.26 mm. I haven't noticed any colour glow in these monitors even though I have tried to see it.

Change the DPI setting.

---

### Post by trotur on 2010-06-09
Thanks for a reply.

> **dcstar said:**
> Change the DPI setting.

I changed DPI setting to 92 that should (?) be the correct value for this monitor. However this doesn't improve text quality. For example, if I write some letters with long vertical edge (e.g. HIJKL|) to terminal window, edges of the letters will be clearly reddish or bluish.

If I set some large value for DPI (110 or more), text will be very large and thus smoothing colors will be unnoticeable. I don't think that this is the way it should be.

I also noted that DPI setting doesn't affect to text on web pages in Firefox. In Firefox menus etc will update according to a new DPI value after restarting Firefox, but web pages looks as they used to be. In Firefox settings (about:config) I changed manually the value of "layout.css.dpi". This settings seems to change size of some text in web pages, but most of the text remain unaffected.

---

### Post by trotur on 2010-06-20
> **trotur said:**
> I just bought a new monitor, Acer H243HX 24" 1920x1080. I have Ubuntu 10.04 and subpixel smoothing enabled with slight hinting and RGB-order (monitor has same RGB-order).

The problem is that fonts seems to have "too heavy" smoothing: **fonts doesn't look black but colourful. Text has almost unnoticeable but very irritating colour glow.**

Solution to my problem: monitor was over-sharp. Above mentioned monitor H243HX lacks of sharpness setting when using DVI-cable. With VGA-cable sharpness can be adjusted.

I did some tests on another monitor, Samsung SyncMaster EX2220, which has more versatile settings. Adjusting sharpness by looking fonts or using [http://www.lagom.nl/lcd-test/sharpness.php](http://www.lagom.nl/lcd-test/sharpness.php) gave me nice and smooth fonts.

---

### Post by Barafu Albino Cheetah on 2010-06-20
Yor problem may lay not in sharpnss or other conventional settings.
It seems your monitor has an unusuall order of color bits. If, for example, most have Blue-Rad-Grenn-B-R-G-B-R-G so on, you may have B-G-R-B-G-R. Subpixel smoothing technology relays on this order. Software can'tr read it from monitor, and has to make assumptions. 
You shoul be able to adjust this order in your software. But I don't know how.

---

### Post by trotur on 2010-06-20
> **Barafu Albino Cheetah said:**
> Yor problem may lay not in sharpnss or other conventional settings.
It seems your monitor has an unusuall order of color bits. If, for example, most have Blue-Rad-Grenn-B-R-G-B-R-G so on, you may have B-G-R-B-G-R. Subpixel smoothing technology relays on this order. Software can'tr read it from monitor, and has to make assumptions. 
You shoul be able to adjust this order in your software. But I don't know how.

In Appearance-preferences subpixel order can be set to RGB or BGR (or to vertical versions of those). RGB-order gives better output on those monitors than BGR. I wonder why those monitors would have some extraordinary subpixel order since they are just basic monitors.

---

