---
title: "Cannot restart with ATI Radeon X1400"
date: 2010-12-23
forum: General Help
---

### Post by sprungfeld on 2010-12-23
Hi,

I have been using the xorg drivers for my ATI radeon x1400 (in a Thinkpad R60) for a while now and never had any problems. In Ubuntu 10.04, however, I had massive performance issues with KMS enabled (crappy sound, bad compiz-performance, very low FPS-rates in 3d games). For that reason I disabled KMS long ago with radeon.modeset =0. This worked perfectly und 100% stable for the last 12 months.

Lately however I upgraded to 10.10. Everything still works fine -  except for the fact, that I cannot restart or shutdown my system via the Gnome Buttons. Instead, I simply am logged out and the login window is showing up again. I searched syslog for any error message - but there isn't any. The problem isnt always there, about 70% of my attempts to shutdown/restart fail completely. Doing a simple sudo reboot works without a flaw.

This corresponds to another problem. When pressing ctrl-alt-f1 to switch to another console, I mostly get strange artefacts on my screen and a completely functionless graphics card. I can switch back to my Gnome Desktop via ctrl-alt-f7, using mouse and keyboard, listening to music - but all I see then is lines and artefacts.

I figured that could have something to do with my KMS being disabled. So I switched that on again - and restart/shutdown worked perfectly, also console switching. Interestingly enough, the problem then seems to be transferred to the booting of my system - because now I get these strange artefacts on every third boot or so the moment the system tries to display the login window. Needless to say that I have the same performance isseus with KMS as in Ubuntu 10.04.

So I dont want KMS enabled. But I also want to shutdown my system correctly and switch between consoles. That problem is driving me crazy - because I cannot find any error message. My feeling is that when shutting down Gnome, something goes wrong with the graphics driver and the shutdown simply is stopped somehow.

Any help appreciated!!

---

