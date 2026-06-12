---
title: "xorg process hits 100% when scrolling"
date: 2012-01-23
forum: General Help
---

### Post by lazermanx2 on 2012-01-23
Hello, I'm using Ubuntu 10.04. I recently installed an nVidia geforce 6200 and added a second monitor. I installed the nvidia drivers (current version) and spanned my X session across both screens.

After doing this I noticed that when I scroll in windows (with or without the scroll wheel) my xorg process hits 100% and scrolling gets really choppy. This happens in Firefox, Chrome, a terminal window, and even in windows running in my Windows XP Virtual machine. It also happens if I only have one program open. 

I disabled the second monitor, it still does it. I turned off all effects under appearance and I get the same results. I turned off subpixel smoothing (as per a recommendation on a forum post) and that didn't work. When I am on my on-board intel card I do not have this issue. I looked a bit online and haven't been able to find a solution.

One thing I noticed is that opengl effects do not seem to be affected. opengl screensavers going across both screens work just fine, Compiz effects work great and games like openarena play fine. It only seems to be when I'm scrolling in a window that this happens. Thinking it may have been a driver issue I updated my x drivers to current and am now on nvidia driver 290.10 and am still seeing the issue.

Does anyone have any ideas on why this would be happening?

---

