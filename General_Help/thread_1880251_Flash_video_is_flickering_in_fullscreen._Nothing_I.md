---
title: "Flash video is flickering in fullscreen. Nothing I have tried is working."
date: 2011-11-13
forum: General Help
---

### Post by amaruq_atka on 2011-11-13
I am using 10.10. When I goto fullscreen the bottom half of the video flickers white for some videos, for others it lags in fullscreen. I have tried a few things, such as disabling compiz, then loading it and using disabling/enabling legacy fullscreen support and Unredirect fullscreen windows. Video driver is the one recommended, flash player was installed from the Ubuntu software center. Some other things I have tried simply did not work, like installing from the terminal, the could never be found. Must be old then. Or, as I like to say it actuality worked, thats why its gone.

---

### Post by Claus7 on 2011-11-13
Hello,

I would advice you to install the proprietary driver of your card along with flash aid. With the latter you will be certain that you have installed the right version of flash system wide.

I would advice you to install flash aid first, which will get rid of mixed flash installations and then proceed switching driver.

Regards!

---

### Post by amaruq_atka on 2011-11-13
> **Claus7 said:**
> Hello,

I would advice you to install the proprietary driver of your card along with flash aid. With the latter you will be certain that you have installed the right version of flash system wide.

I would advice you to install flash aid first, which will get rid of mixed flash installations and then proceed switching driver.

Regards!

Forgot to mention, I did try flash aid. Nothing. And which video driver? I am using the proprietary one that comes recommended. There are two other ones I can try, though not recommended. What configures should I try with them?

---

### Post by ajgreeny on 2011-11-13
I would almost have been surprised if you did not see some degree of flicker with full screen flash;  it is largely the result of flash for linux not using the graphic card to its full extent, and having to use the cpu for graphics instead.

Try using flash-aid but changing the setting for the graphic card rendering;  it may help but will depend on your card and own intrinsic abilities.

---

### Post by Claus7 on 2011-11-13
Hello,

which are your driver's specs on first place? If it is ati I would advice you to choose the tear free option. Do you get the same things while you are trying to open a video full screen?

I'm referring to the driver NOT in the ubuntu repositories.

Regards!

---

### Post by blangston on 2012-04-01
Wanted to share that setting the tear-free option in the the Catalyst Control Center worked for me.  I've got:

[LIST]
[*]Ubuntu 11.10 64-bit
[*]ATI Radeon HD 3450 video card
[*]ATI Catalyst driver 12.3 (March 2012)
[*]Flash plugin 11.2.202.228
[/LIST]
I would get flickering at the bottom of the screen in full screen mode, but that went away once I enabled the tear-free option.

---

