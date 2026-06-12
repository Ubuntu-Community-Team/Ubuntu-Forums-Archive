---
title: "why &quot;gnome-shell --replace&quot; no longer works?"
date: 2010-04-10
forum: General Help
---

### Post by legolas_w on 2010-04-10
Hi,

It is about a month or so that I can not use gnome-shell because when I try to run it using ```
gnome-shell --replace 
``` it does not work and instead shows the following error:


```

do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
    JS ERROR: !!!   REPORTED: 'reserved slot index out of range'
    JS ERROR: !!!   REPORTED: file '(null)' line 0 exception 0 number 166
Failed to init standard javascript classes

Shell killed with signal 6
Cannot register the panel shell: there is already one running.


```

I am using a PPA to have the latest version and unfortunately it does not work anymore.

If you know how to run it or fix this problem, let me know.

thanks.

---

### Post by chriswyatt on 2010-04-10
Is this a community cafe thing?

---

### Post by cariboo on 2010-04-10
This really isn't a cafe question, I'll move it to General Help.

Yesterdays Lucid updates removed gnome-shell as libgjs0 wasn't upgradeable. That problem has now been fixed, reinstall gnome shell, and things should work OK. I just reinstalled gnome-shell and am running it now.

---

