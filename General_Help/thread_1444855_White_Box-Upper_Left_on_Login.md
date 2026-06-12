---
title: "White Box-Upper Left on Login"
date: 2010-04-01
forum: General Help
---

### Post by markschanz on 2010-04-01
Hello. I've been experiencing *major* issues lately. When I try logging in, I get a white box that takes up about 1/4th of the top-left of the screen and the background stays the solid ubuntu orange. After *a ton* of searching and frustration, I found something that worked, but I do not trust it to work again... I tried taking down to shell with ctrl-alt-f1, which worked, installed libesd0 over alsa like a thread I read on here said to do, and cd'd to /etc/init.d, and sudo ran gdm start. This came up with the screen about starting X in one of the areas (Completely forgot all the content, the stuff you switch to with the ctrl-alt-function keys) Anyways, the white screen continued to happen after I logged in on the new thing, and I went back to the shell and just stared at it in frustration :/. After a while, I ctrl-alt-f7'd back to the X that was stuck on the white box, and the white box became some error message about GNOME (I should have taken down the contents), and I was in. It took a few more minutes after everything came up and I went online. It took a few minutes for the login sound to play, oddly enough. Has anybody experienced this problem, and if so, how did you fix it? I'm tempted to just *never* reboot the computer again so I don't have to deal with this, but power outages and such *do* happen ;) Sorry about the vague info, but I was frustrated at the time and didn't retain much of the details about what I was doing :)

---

### Post by Barriehie on 2010-04-01
That happened to me about every other boot and it was an issue with the gnome-settings-daemon.  If that's the issue you're having some of the things in my old post(s) might help.  I never could get it resolved.  Here's the link to my posts.  [http://ubuntuforums.org/showthread.php?t=1379630&highlight=gnome-settings](http://ubuntuforums.org/showthread.php?t=1379630&highlight=gnome-settings)  Sig has my solution.

---

