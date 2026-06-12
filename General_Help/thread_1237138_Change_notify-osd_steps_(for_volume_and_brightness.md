---
title: "Change notify-osd steps? (for volume and brightness)"
date: 2009-08-11
forum: General Help
---

### Post by gfa on 2009-08-11
Hi everyone...

Is there any way to **change the steps** (increment/decrement) from the new **notification system in Jaunty** (notify-osd)???

What I want is to have the ability to change the volume and brightness in smaller steps, because the defaults seems bigger to me.

PS: I've searched for any string in gconf-editor, into Google and this forums, but I can't find any solution...

Thanks.
gFa

---

### Post by therendus on 2009-10-16
> **gfa said:**
> Hi everyone...

Is there any way to **change the steps** (increment/decrement) from the new **notification system in Jaunty** (notify-osd)???


Yo!

Gnome->Configuration Editor(gconf-editor)->/apps/gnome_settings_daemon/volume_step

Gnome->Configuration Editor->/apps/compiz/plugins/obs/screen0/options/brightness_step (dunno if that'll do that for ya, I don't have brightness control)


Daniel

---

### Post by therendus on 2009-10-16
Btw anyone else think the volume scale is a bit off (thus making the mentioned steps needing yet another correction from somewhere)?
It's like halfing the volume downs the audio about 4 times (perceptually).
Compared for eg. to what the totem player would do if you half it's volume (it adjusts the volume correctly) :-\"

As if the algorithmic attenuation is being applied twice in total along the audio pipeline!

---

### Post by gfa on 2009-10-16
> **therendus said:**
> Yo!

Gnome->Configuration Editor(gconf-editor)->/apps/gnome_settings_daemon/volume_step

Gnome->Configuration Editor->/apps/compiz/plugins/obs/screen0/options/brightness_step (dunno if that'll do that for ya, I don't have brightness control)


Daniel

Thanks!!! The setting for volume control worked perfect :) the one for brightness didn't because right now i'm not using compiz i suppose

---

### Post by therendus on 2009-10-16
> **gfa said:**
> Thanks!!! The setting for volume control worked perfect :) the one for brightness didn't because right now i'm not using compiz i suppose

Nice !
You might have luck trying (for whatever you're running):

[LIST]
[*]Open Configuration Editor (GConf)
[*]Find [Ctrl-F]
[*]Enter *_step*
[*]Go
[/LIST]

---

