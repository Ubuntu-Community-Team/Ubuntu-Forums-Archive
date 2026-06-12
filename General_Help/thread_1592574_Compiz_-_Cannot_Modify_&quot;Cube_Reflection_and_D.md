---
title: "Compiz - Cannot Modify &quot;Cube Reflection and Deformation&quot; Settings"
date: 2010-10-10
forum: General Help
---

### Post by 90sgamer on 2010-10-10
This might be a relatively long one, but please read.

I just installed Ubuntu 10.10 on my desktop and installed the AMD restricted drivers (Radeon HD 5770).  I installed compizconfig-settings-manager and compiz-fusion-plugins-extra.  All of the plugins have worked fine so far.  However, while "Cube Reflection and Deformation" works, I cannot change the settings.  Specifically, I tried changing the cube caps from the visually irritating logos to which it defaults to plain white, but the logos stayed.  I also tried removing the annoying "Reflection" option, but to no avail.  I soon discovered that none of my settings would apply to the plugin, although they would display as though they were applied in the settings manager.  Changing the settings in other plugins, like "Desktop Cube," works fine.

So far, I am sticking just with the "Desktop Cube," "Rotate Cube," and "3D Windows" plugins, but I would really like that cylinder.  And I have used Compiz, including the deformation plugin, for years with no difficulty, so I am not a dumb noob at this.  Any suggestions would be much appreciated.

---

### Post by Nugar on 2010-10-17
Hello 90sgamer,

Did you find any answer to this? In my case, the Deformation is disabled.

Cheers,

---

### Post by InaBanina on 2010-11-03
Hi, 

I seem to be having the same problem. I'm using 10.04 though. I could enable "Cube Reflection and Deformation" and the cylinder would work. However, I couldn't modify any of the default settings. I couldn't switch to the sphere and neither could I change the pictures on the cube caps. 

Any ideas on how to remedy this? Thanks!

---

### Post by stinkeye on 2010-11-03
Works fine here with nvidia on maverick.
If you have the compiz ppa enabled, some packages may have changed...maybe???

---

### Post by InaBanina on 2010-11-04
I wouldn't know. :( Oh well, it's not that important. I'll live if I can't enable the sphere on my desktop, lol. I just wanted to know why it wasn't working. 

Thanks for the response! :)

---

### Post by MsKK on 2010-11-16
I have the same problem with 10.04. cannot change the defaults settings (although I can enable and disable it). I just cannot customize.

---

### Post by tunist on 2010-12-01
i have all features working ok in 10.10 (that i've looked at so far).. 
however, the top and bottom caps do not change when i change the values of their image paths in either the 'cube reflection and deformation' panel or in the main cube settings panel.

if i disable 'reflection and deformation' the cap images do change.. 
so it seems the issue is with the r & d module.

---

### Post by sedated on 2011-06-09
If you just type the below code all the settings of Cube Reflection and Distortion start to apply. Don't how it happens, but it just happened  for me. :confused:

```
compiz --replace &
```I know this thread is old, but i had the same problem, and since this page was suggested by google before than the other page with solution to the problem, i thought solution should exist here as well.

---

### Post by will5381 on 2011-06-28
That worked for me - thanks so much!

---

### Post by Ominous Omnivore on 2012-06-20
A year later and 12.04 

compiz --replace &
did the trick for me as well. Thank you so much.

---

### Post by lisati on 2012-06-20
> **Ominous Omnivore said:**
> A year later and 12.04 

compiz --replace &
did the trick for me as well. Thank you so much.

Back to sleep, old thread!

---

