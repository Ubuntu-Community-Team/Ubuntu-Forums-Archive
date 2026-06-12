---
title: "Ubuntu won't boot normally or in recovery, except with Ctrl C"
date: 2012-07-12
forum: General Help
---

### Post by ervinshiznit on 2012-07-12
I have no idea how this is happening, but here goes.

When I try to boot Ubuntu 12.04 normally, I am presented with a blank purple screen.  It has no response to keyboard or mouse input.

In recovery mode, I have tried fixing broken packages, reinstalling x, removing the AMD graphics driver (I have a Radeon HD 7750).  I tried to boot into failsafeX, and that doesn't work.  When I try to run it in low graphics settings for just one session, it says that it will restart the display in a minute, but it never does.  I press ok and I come back to the recovery menu.

Here's the strange part:  If I say repair broken packages, and then while its looking for packages I ctrl c to quit, it boots!  I then proceeded to reinstall the proprietary AMD graphics drivers using the instructions here: [http://www.upubuntu.com/2012/06/install-amd-ati-catalyst-126-display.html](http://www.upubuntu.com/2012/06/install-amd-ati-catalyst-126-display.html)

I thought perhaps it was a graphics driver problem, but nope, that didn't let me boot normally.  I booted into recovery mode and used the ctrl c trick again, and now I have my triple monitor setup properly configured with the AMD catalyst drivers.

So the question is, how do I get this to boot normally?  And why on earth is this even possible?  I'm pretty new to Linux but this is quite confusing.

---

