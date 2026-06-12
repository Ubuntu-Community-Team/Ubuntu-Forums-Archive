---
title: "Trouble with nvidia drivers in Ubuntu 11.04"
date: 2011-05-07
forum: General Help
---

### Post by jcd29 on 2011-05-07
I have a friend's Toshiba Satellite A665, and just installed Ubuntu 11.04 in it, but a screen popped up announcing I didn't meet the graphics requirements for Unity, or something similar.

So I go to System -> Administration -> Additional Drivers

And check that the NVIDIA accelerated graphics driver (version current) is there, but below it says the following:

**This driver is activated but not currently in use**

Now I've tried a few different things, like deleting it and installing nvidia current from synaptic, but nothing. The only thing that came close to working was just removing this driver from the Additional Drivers menu, and rebooting. Then I could use Unity. The thing is I don't have the nvidia proprietary driver anymore when I do that, which is what I want.

Any way to solve this particular problem?

---

### Post by timgood on 2011-05-07
This is a bug that has been reported but does not, as yet, have a fix. However, the good news is that your driver is activated and is in use, despite what the box says. This is why you can boot into Unity which uses Compiz and relies on the Nvidia driver.

Hope this helps.

---

### Post by jcd29 on 2011-05-07
> **timgood said:**
> This is a bug that has been reported but does not, as yet, have a fix. However, the good news is that your driver is activated and is in use, despite what the box says. This is why you can boot into Unity which uses Compiz and relies on the Nvidia driver.

Hope this helps.

I don't think it's in use. I can only boot into Unity when I remove the driver. And even then, I can't even access any extra effects in Appearance.

I'm guessing it's something that'll be fixed in updates?

---

### Post by helmo42 on 2011-06-22
The bug you are referring probably is:
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788)

---

### Post by wildmanne39 on 2011-06-22
> **jcd29 said:**
> I don't think it's in use. I can only boot into Unity when I remove the driver. And even then, I can't even access any extra effects in Appearance.

I'm guessing it's something that'll be fixed in updates?Hi, you said you installed one through synaptic,  when you did that, then you probably had two installed at the same time because that happened to me, it only shows one in additional drivers as activated, but if two are installed then to are being used and that causes problems, also you may have to test and see which one is better for your system the newer one for mine is buggy I had to go back to the old one, and I have the cube and many effects in natty working great. Check synaptic and make sure only one is installed and if you can get to the unity desktop it is activated.

---

