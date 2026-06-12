---
title: "TwinView - Cannot Move Windows Across Monitors"
date: 2009-11-29
forum: General Help
---

### Post by TannerLD on 2009-11-29
Hi,

I'm using two Dell E198FP monitors and a NVidia GeForce 9800 GX2 graphics card to have dual monitors in Ubuntu. I have tried Xinerama, but certain programs do not run using that.

Anywho, I'm now running TwinView, which works perfectly fine, but - I can't move windows from one monitor to the other. What it does is just move the window to the next Virtual Desktop in that monitor (which is really strange to see). I've read up and apparently either TwinView is supposed to make one giant monitor for X-Windows or something like that (I may have gotten it confused, eh).

Anywho, is there a way to "fix" it so I can still use TwinView and move windows across my monitors?

Thanks
-Tanner

---

### Post by Grenage on 2009-11-29
It sounds like it's using seperate X instances, try deleting your config and starting again (it's a quirky beast).

---

### Post by howefield on 2009-11-29
At the risk of stating the obvious, what happens if you move the window to the other side of the screen ?

In other words, have you told nvidia-settings where each monitor is in relation to each other ?

Sorry if that is crazily simple and of course you tried it.

---

### Post by TannerLD on 2009-11-29
> **Grenage said:**
> It sounds like it's using seperate X instances, try deleting your config and starting again (it's a quirky beast).

Eh, not sure how to start again - I'm happy enough that its running with my graphics card. That alone took a few months of understanding.

> **howefield said:**
> At the risk of stating the obvious, what happens if you move the window to the other side of the screen ?

In other words, have you told nvidia-settings where each monitor is in relation to each other ?

Sorry if that is crazily simple and of course you tried it.

If I have a terminal window on the left monitor and if I drag it as though I want it on the right monitor, the left monitor shifts to the next virtual desktop (I think Compiz may be doing that, idk - long time since I last used that), while the right monitor stays the same w/ no change.

Yeah, nvidia-settings knows where everything is.

I'm not sure if this makes a difference, but I did this TwinView setup by hand (probably the root cause). I did that because the option for TwinView in selecting the display configuration in nvidia-settings is grayed out. Forgot to mention that in my first post. Probably a problem of it generating the xorg.conf vs me.

Thanks
-Tanner

---

### Post by scouser73 on 2009-11-29
Please follow these instructions for setting up dual monitors.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - **X Server Display Configuration** will now start, now you can set up your monitors to your liking

**3** - Once you have done so click **Apply** then click **Save To X Configuration File**

You will now have dual monitors working.

**Set the position to Absolute**

---

### Post by TannerLD on 2009-11-29
> **scouser73 said:**
> Please follow these instructions for setting up dual monitors.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - **X Server Display Configuration** will now start, now you can set up your monitors to your liking

**3** - Once you have done so click **Apply** then click **Save To X Configuration File**

You will now have dual monitors working.

**Set the position to Absolute**

As I said in my previous post, I cannot select TwinView as a option to configure the displays (it is grayed out). The only options I have are "Separate X Screen" or "Disabled". Xinerama will not work for what I run.

-Tanner

---

### Post by TannerLD on 2009-12-03
Anyone know what may be causing my problem?

Thanks
-Tanner

---

### Post by WylieE on 2010-10-04
> **TannerLD said:**
> As I said in my previous post, I cannot select TwinView as a option to configure the displays (it is grayed out). The only options I have are "Separate X Screen" or "Disabled". Xinerama will not work for what I run.

-Tanner


I am also having the same problem (and I also edited xorg.conf by hand).  I can (finally) get the graphics cards up and running, but I can't enable TwinView from the nvidia-settings route.

---

### Post by f0rcegr0wn on 2010-11-25
Long story short, multiple video cards is a no-no for ubuntu. I've wasted almsot 3 days looking into this and although Xinerama works (and you need to set everything to seperate X screen) the following also need to apply:

Compatibility between the cards so that the nvidia driver can use both of them.
Desktop effects don't work (compiz).

I too am frustrated on this as I can't show off Ubuntu in the office with my 3 monitor and 2 video card setup.

---

