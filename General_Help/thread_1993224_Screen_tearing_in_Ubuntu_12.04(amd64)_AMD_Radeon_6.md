---
title: "Screen tearing in Ubuntu 12.04(amd64) AMD Radeon 6410d"
date: 2012-06-01
forum: General Help
---

### Post by PhantomTurtle on 2012-06-01
I have found that when I am browsing the web (in Firefox or Chrome), I have this screen tearing issue. It is also visible on Youtube, Vimeo and other video site videos(flash and html5, little to none in flash). I can notice it the most on html5 videos. I have the AMD Radeon proprietary drivers installed(using Additional Drivers). My video card is AMD Radeon 6410D, processor - AMD A4-3400 APU. I am running the 64-bit version of Ubuntu and do not mind having to reinstall. (I don't know if this will help but this computer also runs Windows and I have not experienced this problem with Windows. A CD came with windows drivers for the APU).

EDIT: This also happens when I watch videos offline on media players such as VLC and Totem.

---

### Post by brainwash on 2012-06-01
Open Catalyst Control Center, switch to Display Options and enable Tear Free Desktop mode.

---

### Post by PhantomTurtle on 2012-06-01
> **brainwash said:**
> Open Catalyst Control Center, switch to Display Options and enable Tear Free Desktop mode.

That works, Thank you. Are there any side effects to this? Also I tried removing the proprietary drivers and used the drivers that were included with Ubuntu, and this did not happen with those. So it's probably  a problem with the proprietary drivers, hopefully they will fix it. Thank you again for your answer.

---

### Post by brainwash on 2012-06-02
> **PhantomTurtle said:**
> That works, Thank you. Are there any side effects to this?
Selecting the Tear Free Desktop mode enables VSync and even Triple  Buffering, so your GPU will use more VRAM and do additional processing.  This reduces tearing in 2D and 3D applications. However, for example,  you might notice a slight mouse/keyboard input lag while playing Games.

If  you use the open source driver instead, KMS (enabled by default) should  detect the necessary settings for your GPU and therefore eliminate  tearing.

---

### Post by PhantomTurtle on 2012-06-02
> **brainwash said:**
> Selecting the Tear Free Desktop mode enables VSync and even Triple  Buffering, so your GPU will use more VRAM and do additional processing.  This reduces tearing in 2D and 3D applications. However, for example,  you might notice a slight mouse/keyboard input lag while playing Games.

If  you use the open source driver instead, KMS (enabled by default) should  detect the necessary settings for your GPU and therefore eliminate  tearing.

Thank you for answering my question. I don't play games much so I guess I'll be fine then.

---

### Post by Houmie on 2012-06-05
I had the exact same problem with tearing in online and offline videos. That solved. Thank you so much.

---

### Post by framebuffer on 2012-07-01
> **brainwash said:**
> Open Catalyst Control Center, switch to Display Options and enable Tear Free Desktop mode.

I am using catalyst 12.4

When I go to the catalyst control centre, there is no "Display Option".

I remember it use to be there briefly for prior versions of Catalyst on Ubuntu 10-11. But now I cannot see it any more.

I am using Ubuntu 12.04, Intel 3000/ATI 6630M Hybrid

If I try to enable tear free desktop from command line, I get "You are running in low graphics mode..." and I cannot log in. I have to reinitialize aticonfig.

How to enable tear-free desktop?

---

### Post by yochaigal on 2012-07-09
Probably you have a switchable graphics card (as do I) and the tearing option is somehow unavailable!

---

