---
title: "Nvidia Confusion"
date: 2011-04-08
forum: General Help
---

### Post by dh04000 on 2011-04-08
Dell finally got my broken laptop back to me and upgraded my ati x1400 to a nvidia 7900gs !!!!

So of coarse I installed the proper driver and are trying to install steam and tf2.

I ran into an issue of playonlinux complaining that I'm not directly rendered, even though I have compiz on.....

Here's the glxinfo output, only putting the useful part.

> ~$ glxinfo
name of display: :0.0
Error: API mismatch: the NVIDIA kernel module has version 195.36.15,
but this NVIDIA driver component has version 195.36.24.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:

I'm very confused how I have compiz on and I'm not direct rendered. Is there as kernel issue? I see an api issue. Can someone help me?

---

### Post by Dutch70 on 2011-04-08
You can change Compiz to direct or indirect rendering. Click the compiz fusion icon to get it on your panel, then right click it & go to compiz options, make sure indirect rendering is not checked.

---

### Post by dh04000 on 2011-04-08
> **Dutch70 said:**
> You can change Compiz to direct or indirect rendering. Click the compiz fusion icon to get it on your panel, then right click it & go to compiz options, make sure indirect rendering is not checked.

I don't think the issue is in compiz.... check the glxinfo output.

EDIT:In the fusion icon, the compiz options are loose binding and indirect rendering.

---

### Post by Dutch70 on 2011-04-08
Yeah, sorry I don't know much about that. 

You had mentioned not understanding how you could have Compiz on and not have direct rendering. I was just saying you can choose between direct or indirect rendering from Compiz options. Of course, you would choose direct rendering by unchecking direct rendering. Doesn't look like that will help though.

---

### Post by dh04000 on 2011-04-08
> **Dutch70 said:**
> Yeah, sorry I don't know much about that. 

You had mentioned not understanding how you could have Compiz on and not have direct rendering. I was just saying you can choose between direct or indirect rendering from Compiz options. Of course, you would choose direct rendering by unchecking direct rendering. Doesn't look like that will help though.

I clicked loose binding and now my glxinfo says I have direct rendering. Go figure?

Thanks for the help!

---

### Post by Dutch70 on 2011-04-08
LOL...Great!!!

---

