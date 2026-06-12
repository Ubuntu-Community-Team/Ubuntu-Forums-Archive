---
title: "Screen doesn't appear to 'fit'"
date: 2011-03-08
forum: General Help
---

### Post by matthewcb on 2011-03-08
Hi,

Just installed ubuntu 10.10 on an Acer Revo 3700 and works pretty well so far.

However, I have a problem in that the display appears to be slightly larger than the screen.

The resolution is set @ 1920 x 1080 and the dimensions of the screen are  the same.  The drivers are the latest NVidia ones obtained from the  web.

There's no option that I can see to shrink the edges of the display so I'm pretty much stuck.

I can click 'above' the screen and then see the menus, but I can't figure out how to scale the screen properly.

Any ideas?

Thanks in advance.

---

### Post by jerome1232 on 2011-03-08
I swear there is an utility provided by the nvidia tools which can do that. Have a look under system-administration or system-preferences for nvidia x configuration or something similar.

---

### Post by matthewcb on 2011-03-08
Hi, thanks for the reply.

Yes, there is a 'Nvidia X Server settings' app.  But I can't locate an option to change the display in the way I need to.

I can change the resolution and, strangely enough, more of the toolbar is displayed the lower the resolution.

But I can't see where I can change the screen scaling.

Edir: found it!  But it was a devil to find...

Under DFP-0 (<monitor name>), there's a setting called 'overscan compensation'.
That fixes it.
It's almost the last setting available.
Thanks again for the help.

---

