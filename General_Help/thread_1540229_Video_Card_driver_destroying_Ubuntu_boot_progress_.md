---
title: "Video Card driver destroying Ubuntu boot progress sequence"
date: 2010-07-27
forum: General Help
---

### Post by Sublymonal on 2010-07-27
I know it's an odd thing to like, but one of my favourite things about Ubuntu is the boot progress sequence [the part where it says "ubuntu" and underneath are the dots that fill with orange]. I first noticed it in my wubi install. Later I noticed it had started to bug, or not work at all and the resolution was way off. I just tacked it down under "wubi isssues".

Now, however, I have a full install on a dedicated partition. And the problem persists. I have tacked it down to the driver for my video card [nVidia 9600m GS]. When I disable the driver, it somewhat returns to normal [it works fine on shut down, but boot up is still buggy]. However, this makes Docky complain about compositing [it will still work, but there's a black void around it] not being enabled. I also assume that lacking the driver will cause problems if I try to do anything 3D.

Honestly, I'm not gonna be doing anything 3D with Ubuntu. Win7 covers me there. Is there any way to enable compositing without having the driver installed?

---

### Post by themusicalduck on 2010-07-27
You could try running Metacity compositing. I don't know how well it works with the Nouvaue driver (the default if the normal one isn't enabled).

You can switch it on by running this command ```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true

``` in a terminal (Applications > Accessories > Terminal). Or by downloading and using Ubuntu Tweak if you'd prefer [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

You can disable it with ```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool false

```

The reason the boot screen is ugly is because the Nvidia proprietry drivers don't support a feature that Plymouth needs. If you do want to use those drivers, there is a workaround for it which worked for me here - [http://www.ubunturoot.com/2010/04/how-to-get-plymouth-working-with.html](http://www.ubunturoot.com/2010/04/how-to-get-plymouth-working-with.html)

but for someone else it broke their bootup, so only try it if you really want to and can fix it if needed.

---

