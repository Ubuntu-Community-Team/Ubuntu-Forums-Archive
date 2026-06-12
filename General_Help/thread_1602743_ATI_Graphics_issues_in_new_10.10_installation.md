---
title: "ATI Graphics issues in new 10.10 installation"
date: 2010-10-21
forum: General Help
---

### Post by Max_Mackie on 2010-10-21
Hey all,

I just upgraded to 10.10 from 10.04 (using the update manager. Back in 10.04 I was using ATI Catalyst something (also called fglrx). When I restarted my computer for the upgrade, my resolution and my dual screens weren't working. I went in Ubuntu's screen resolution menu and unchecked the "Mirror Screens" option and tried to set the right resolutions for my screens, but the right resolutions were not available. 

I tried going through the ATI Catalyst menu and enabled a dual screen option from there. I rebooted and didn't get any graphics at all. I eventually changed the boot command from "[...] ro quiet splash" to "[...] ro nomodeset single".

I brought me to the GRUB recovery mode for my ubuntu partition and I chose some option with reduced graphics (which is what I'm currently using).

Not fglrx isn't installed and when I try to reinstall it I get a weird error message, but it still installs.

I tried fully removing fglrx and got this error:
```
dpkg: error processing alsa-utils (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 alsa-utils
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Please help if you can, I'm desperate.

---

### Post by PaulW2U on 2010-10-21
The bug you're seeing is unrelated to your ATI driver. The bug was fixed in the last few hours and a new version of alsa-utils will be available shortly. Ignore the error messages for now, they'll go away when you download the update.

---

### Post by Max_Mackie on 2010-10-21
Awesome thanks!
I'm guessing that the update isn't in the repos yet? If they are do I just "sudo apt-get update"?

And that means I still have the graphics issue. Any idea?

---

### Post by PaulW2U on 2010-10-21
> **Max_Mackie said:**
> Awesome thanks!
I'm guessing that the update isn't in the repos yet? If they are do I just "sudo apt-get update"?

That's right.

> **Max_Mackie said:**
> 
And that means I still have the graphics issue. Any idea?

Can't help on that on that one, sorry.

---

