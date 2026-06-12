---
title: "Smoother Window Dragging w/ Compiz"
date: 2009-12-14
forum: General Help
---

### Post by darkestfright on 2009-12-14
I don't know if anyone else has had this issue, but since this is the Ubuntu community I'd figure I'd share my experiences/solutions with everyone.

I noticed that window dragging seemed very choppy, even when using Compiz Fusion.
I've tried other distros on the same machine and have had significantly increased visual performance. I really enjoy using Ubuntu though, because it's simply the most polished distro I've used (in my experience).  So I opened up CCSM and started digging around in the General Options menu.

In the "Display Settings" tab, I disabled the "detect refresh rate" and enabled "Sync to VBlank" and in the "Refresh Rate" slider, I increased it from what was defaulted to 50 to 120.

I am also using the 190.42 proprietary Nvidia driver, with "Sync to Vblank" enabled in the Xvideo settings.

I now have identical visual performance to the other distros I was using, probably even better.  I hope this helps someone, because I know it's been bugging me for an extremely long time.

---

### Post by Killbam on 2011-10-31
Very nice, in 11.10 with Compiz as of Oct. 31st, 2011 the options have changed a bit.

Sync to Vblank can be founder under General - OpenGL and is already enabled.

Detect Refresh Rate and Refresh Rate can be found under General - Composite.  I can confirm that disabling Detect Refresh Rate and increasing the Refresh Rate to 120 makes things look like it should!

---

### Post by stinkeye on 2011-10-31
This is a two year old post and the OP's solution makes no 
difference here.

---

