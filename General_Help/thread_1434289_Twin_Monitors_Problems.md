---
title: "Twin Monitors Problems"
date: 2010-03-20
forum: General Help
---

### Post by Hado on 2010-03-20
I have ubuntu 9.10 on my desktop computer.
It has two monitors; and I have an nVidia graphics card.
I can activate both monitors to run simultaneously using the twinview option
in the nvidia display options.

The problem is that whenever a window pops up on the display, it sets it precisely in the center of both screens such that it is fragmented on both.  I want it to spawn in the center of one of the two screens.

The other problem is that when i shut down the computer, I have to reset the display options in order to get both monitors working again.

How do I get Ubuntu to run both monitors even upon restarting?
And how do I get menus that appear, not to be in the exact center of both displays?

---

### Post by scouser73 on 2010-03-20
> **Hado said:**
> I have ubuntu 9.10 on my desktop computer.
It has two monitors; and I have an nVidia graphics card.
I can activate both monitors to run simultaneously using the twinview option
in the nvidia display options.

The problem is that whenever a window pops up on the display, it sets it precisely in the center of both screens such that it is fragmented on both.  I want it to spawn in the center of one of the two screens.

The other problem is that when i shut down the computer, I have to reset the display options in order to get both monitors working again.

How do I get Ubuntu to run both monitors even upon restarting?
And how do I get menus that appear, not to be in the exact center of both displays?

> The problem is that whenever a window pops up on the display, it sets it precisely in the center of both screens such that it is fragmented on both.  I want it to spawn in the center of one of the two screens.

Follow the instructions I have set out below and set the position to **Absolute**.

Please follow these instructions for setting up dual monitors.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - **X Server Display Configuration** will now start, now you can set up your monitors to your liking

**3** - Once you have done so click **Apply** then click **Save To X Configuration File**

You will now have dual monitors working.

---

### Post by Hado on 2010-03-20
I tried what you said and when i went to save the displays positioning i received this message.

"Failed to parse existing X config file '/etc/X11/xorg.conf'!"

Just so you know i tried to make my samsung (positioned to the left) as the absolute x config at +0 +0.  My sony display is on the right and i used the relative positioning to the right.  Then i clicked save to X config file and BAM error message.

So now what?

---

