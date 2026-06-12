---
title: "How To Fix Unity Effects Lag?"
date: 2011-07-10
forum: General Help
---

### Post by SamirGhobril on 2011-07-10
Hey guys,

I've recently installed ubuntu 11.04, and I actually liked Unity (although many others prefer Gnome), but there seems to be a lag problem. Every time I press the super button to bring out the Dash, or Super+W to show all windows, or any other action that involves some sort of effect, the effect lags a bit, and it could get really annoying.

I've seen a fix using CompizConfig Settings Manager, but that doesn't seem to work for me.

I've got a NVidia 9800 GT 1 GB video card, a 2 GB Ram, and not sure about the CPU (if you need it, tell me and I'll figure it out).

Any help would be appreciated

Thanks in advance.

---

### Post by wojox on 2011-07-10
Are you using the NVidia driver or nouveau?

In Additional Drivers what are you choices for drivers?

---

### Post by wildmanne39 on 2011-07-11
> **SamirGhobril said:**
> Hey guys,

I've recently installed ubuntu 11.04, and I actually liked Unity (although many others prefer Gnome), but there seems to be a lag problem. Every time I press the super button to bring out the Dash, or Super+W to show all windows, or any other action that involves some sort of effect, the effect lags a bit, and it could get really annoying.

I've seen a fix using CompizConfig Settings Manager, but that doesn't seem to work for me.

I've got a NVidia 9800 GT 1 GB video card, a 2 GB Ram, and not sure about the CPU (if you need it, tell me and I'll figure it out).

Any help would be appreciated

Thanks in advance.

Hi, is this the instructions you have already seen? if not do what it mentions it helps in a lot of cases.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)
Also with my nvidia card I have to use the older driver, the newer ones with my card and natty do no play well together. The one in additional drivers is usually the best to use but not in all cases.

---

### Post by SamirGhobril on 2011-07-11
> **wojox said:**
> Are you using the NVidia driver or nouveau?

In Additional Drivers what are you choices for drivers?

In additional drivers I've got NVidia accelerated graphics driver (version current), although it says: This driver is activated but not currently in use.

---

### Post by wildmanne39 on 2011-07-11
> **SamirGhobril said:**
> In additional drivers I've got NVidia accelerated graphics driver (version current), although it says: This driver is activated but not currently in use.Hi, that is just a bug that shows it is not being used it really is if you can see the unity desktop. Did you check out the link in my other post that usually fixes the lag with nvidia drivers, it did with mine, I also have a nvidia card 6150 I have to use the 173 driver because the current one made my system lag and made my windows turn white.

---

### Post by SamirGhobril on 2011-07-13
> **wildmanne39 said:**
> Hi, that is just a bug that shows it is not being used it really is if you can see the unity desktop. Did you check out the link in my other post that usually fixes the lag with nvidia drivers, it did with mine, I also have a nvidia card 6150 I have to use the 173 driver because the current one made my system lag and made my windows turn white.

Yeah I've tried it and it didn't work. I have the latest drivers. Do you think installing the 173 driver will fix it?

---

### Post by Frogs Hair on 2011-07-13
> **SamirGhobril said:**
> Yeah I've tried it and it didn't work. I have the latest drivers. Do you think installing the 173 driver will fix it?

The 173 driver will set you to choppy slow motion . I can't even use the 173 on my 8 series card . You could try this PPA for the latest driver . [http://www.multimediaboom.com/install-nvidia-driver-ubuntu-1-04-11-10-ppa/](http://www.multimediaboom.com/install-nvidia-driver-ubuntu-1-04-11-10-ppa/)

---

