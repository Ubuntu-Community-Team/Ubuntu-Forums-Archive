---
title: "Setup Dual monitor display"
date: 2009-11-29
forum: General Help
---

### Post by Dispatch630 on 2009-11-29
Hey,

I am a noob sorry.  I have jackelope or something like that.  I want to setup a dual monitor display but when i plug in both monitors to the splitter they both display the same thing.  Its just mirroring on both screens.  Can anyone please help me.  I appreciate your guidance and patience in advance.

Best,
Matt

---

### Post by SuperSonic4 on 2009-11-29
What is your video card manufacturer

---

### Post by fluffman86 on 2009-11-29
> **Dispatch630 said:**
> ..the splitter...
That's your problem.  You can't use a splitter and a single video card; it will just split the same signal into 2 different places.

You'll need either a single video card with 2 outputs on it, or 2 video cards.

---

### Post by scouser73 on 2009-11-29
**[COLOR="Red"]For nVidia Graphics Cards Only[/COLOR]**

Please follow these instructions for setting up dual monitors.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - **X Server Display Configuration** will now start, now you can set up your monitors to your liking

**3** - Once you have done so click **Apply** then click **Save To X Configuration File**

You will now have dual monitors working.

---

### Post by audiomick on 2009-11-29
First, fluffman is right.

Second, scouser73's advice assumes that the proprietary driver is installed.

---

