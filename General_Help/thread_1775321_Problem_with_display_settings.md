---
title: "Problem with display settings"
date: 2011-06-04
forum: General Help
---

### Post by Robawtic on 2011-06-04
So my problem is on bootup and shut down I get the 1. analog input cannot display this video mode. I've got a dell monitor nvidia graphics card... Don't really know how to provide much more info than that. from what i've searched on the net is that it probably has to do with the refresh rate. Any help would be greatly appreciated.

---

### Post by wolfen69 on 2011-06-04
Have you installed the nvidia driver?

---

### Post by Hedgehog1 on 2011-06-04
For many folks, this is cause by GRUB setting too high a resolution.

You can force the new grub to use a lower resolution, and this usually solves the symptom:

```
gksudo gedit /etc/default/grub
```

[COLOR="Red"]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR="red"]to this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR="red"]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```


***The Hedge***

:KS

---

### Post by Cathhsmom on 2011-06-16
I just wanted to say thank you Hedge Hog 1.  I had this identical problem on my daughter's computer and your solution worked like a charm.:D

---

### Post by sprankton on 2011-06-25
I had a similar problem and am just using Lucid right now.  I'm wondering, is this something that would be fixed in a future upgrade or is it just ubuntu's way of saying I need a new monitor?

---

