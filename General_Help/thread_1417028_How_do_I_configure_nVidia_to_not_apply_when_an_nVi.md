---
title: "How do I configure nVidia to not apply when an nVidia card isn't present?"
date: 2010-02-26
forum: General Help
---

### Post by thegamefreak0134 on 2010-02-26
I've been pulling my hair out over this one for a couple of days now, google is no help.

I've created a wonderful (until this issue) portable copy of Ubuntu linux that will boot on mostly anything by using a USB enclosure for my laptop's 80GB SATA drive. It's just a normal installation, since the external drive is fast enough to not need Casper or anything. So far so good, it boots and runs on almost everything, and on non-nVidia card setups was even detecting the drivers, or letting me install the required drivers for hardware acceleration and compiz. Because you know, the wobble windows are the most awesome thing ever.

Anyway, my desktop machine had an nVidia card, so I'm thinking, sure, I'll just install the nVidia drivers like before and everything will work happily. Not so-- now the desktop and any other nVidia cards work great, but it seems to have completely disabled any other graphics cards. When the kernel module detects that an nVidia card isn't present, it shoots up this nasty little dialog box giving me the option to boot into "low graphics" mode, which doesn't even allow me to use the correct screen resolution, much less see the installed graphics card and try to configure a driver for it.

Is there any way to configure Ubuntu (with the dreaded nVidia kernel module) so that it can use nVidia's drivers when an nVidia card is present, and default to the normal (not low-graphics) setup in other cases, so that it has a fair chance of using what's actually present? I'm not afraid to muck with config files, I just don't know the underlying system well enough to feel comfortable diving in without a push in the right direction.

Thanks guys!

---

