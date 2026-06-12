---
title: "Problem with FF4, YouTube preview images, DNS settings."
date: 2011-05-16
forum: General Help
---

### Post by brntoki on 2011-05-16
XUbuntu 10.04 64bit

I had off and on problems with YouTube preview images (thumbnails) for a while, but was able to get them to work while using FF-3.16.xx. I upgraded to FF-4 and the thumbnails disappeared again. I tried many, many things to get them to work (FlashAid which usually fixes anything Flash related, disabling all add-ons, fresh installs, new profiles, etc., etc.), but finally decided to try different browsers. Unfortunately, I got the same thing.

Upon changing the proxy settings in FF to auto-detect instead of the default of "No-proxy", the thumbnails immediately showed up beautifully, but only for a while. Playing around with Chromium I found that, as I expected, ytimg.com serves the thumbnail images. More specifically, they are served from i1.ytimg.com, through i4.ytimg.com. Plugging those URLs into FF gave me 404 errors. Obviously, then, this is where the problem was. But why would that happen? Firefox was updated, but my DNS servers were the same (automatic DHCP). I changed to automatic DHCP with addresses, and plugged in OpenDNS servers, and now everything works fine. Plugging in i1.ytimg.com, for example, I get the default placeholder thumbnail as should be expected. Note that I also changed FF back to its default of "No-proxy".

Any ideas why this may have happened? I'm currently able to use my internet without trouble, but I wanted to bring this up so people would be aware of potential issues from other users, and to help me understand what may have gone wrong for future troubleshooting adventures.

Thanks!

---

