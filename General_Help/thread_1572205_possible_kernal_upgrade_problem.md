---
title: "possible kernal upgrade problem"
date: 2010-09-10
forum: General Help
---

### Post by alliance1975 on 2010-09-10
In an effort to remedy problems with my ati radeon xpress 200m video I recently upgraded my kernal from 2.6.32 to 2.6.33. It resulted in a delayed bootup of my laptop with a seeming error that included text like "pm2 null fid, mounting/non, dev not found". But then it boots up and apparently no problem. I can only get snippets of the message since it does not last that long. Can someone help me. Do I need to get the entire text or can I go to a specific *.log that will contain this text/message?

The commands I followed are from another thread entitled" Graphics Problems with ATI Radeon Xpress 200M in Ubuntu 10.04"

I dont know if this will help you guy, but I was experiencing many compiz crashes and weird lines in Firefox ( I couldn't open more than 2 tabs without compiz crashing ) I found a bug in launchpad and one of the commenter's said that a patch was made upstream to the radeon DRM ( it was a bug with this ) in the kernel. He gave a link to a ppa for the patch, but when i went there I couldn't find the patch. So I ended up installing the 2.6.33 kernel and now I have no problems at all. Been running for 5 hours and every virtual desktop has a window open.

If you decided to install the kernel you must get

linux-headers-2.6.33-020633_2.6.33-020633_all.deb
linux-headers-2.6.33-020633-generic_2.6.33-020633_i386.deb or amd64 if you run 64 bit Ubuntu
linux-image-2.6.33-020633-generic_2.6.33-020633_i386.deb or amd64 if you run 64 bit Ubuntu

and install in that order. You can get those debs here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/)

I'm running an ATI Radeon Xpress 200 chipset so i think this might help.

I copied a line from my kern.log as follows"
Sep 10 19:23:25 hpdv5k kernel: imklog: Cannot read proc file system, 1.

---

### Post by alliance1975 on 2010-09-10
bump

---

### Post by alliance1975 on 2010-09-11
Thanks for the help everyone.

---

