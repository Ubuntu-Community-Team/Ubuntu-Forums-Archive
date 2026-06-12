---
title: "Video Output Help"
date: 2009-10-13
forum: General Help
---

### Post by tehfade on 2009-10-13
Hi, all. This is, I think, my second post on these forums, but I've lurked for a while, and you guys are great! I'm pretty new to Linux and without this forum, I'd have run away screaming and tearing my hair out a *long* time ago.

Anyway, I've got a problem that I don't even know where to begin on. I've built a media center pc/server running Xubuntu. It was originally to be a headless BitTorrent and backup box, but I've sort of loaded the kitchen sink on there (ssh, apache, subversion, vsftpd, rsync, torrentflux....) and stuck it under my TV. I'm thinking of throwing a tv tuner card in there and screwing around with Mythbuntu. It's been a fun project so far.

The problem is this: I'm running an Asus micro-ATX motherboard that has VGA, DVI, and HDMI outputs. Since it's now under my TV, and I actually want to use my TV as a display, I really, really want to use the HDMI (Or the DVI, failing that) for output. But there's no video signal on those, and I don't even have a clue where to start on figuring out how to get them to work. Right now, I only have video through the VGA port.

I forget the model of the motherboard, but I'll post it when I get home and can look it up. For now, I'm at school and I have shell access, so if a dmesg or lspci or something would be helpful, I will be happy to post it.

Edit: The motherboard is either an Asus M3N78-PRO or M3N78-EM, with a GeForce 8200 graphics chipset.

---

### Post by P4man on 2009-10-13
did you install binary nvidia drivers ? My laptop with a nvidia 8600 has hdmi, and if I connect it to my tv, it just works. You probably have to switch your tv input to hdmi if it doesnt do so automatically, and possibly you may have to enable the tv as display in nvidia x server settings (system > administration > nvidia X server settings).

---

### Post by tehfade on 2009-10-13
My TV is definitely set correctly...I can get it working with the same cable with my Xbox, so it's not the cable or the TV settings. I installed the Nvidia drivers with the "restricted drivers mnanager" or whatever it is that comes up on a fresh install to tell you you can use restricted drivers...is that what you mean, or should I attempt to install them manually? 

Also, when I run nvidia-settings, I get a message that says I "do not appear to be using the Nvidia X driver". It suggests running nvidia-xconfig as root and restarting X. I've done this, but still get the same message. Any ideas on that, or if it's related?

---

### Post by P4man on 2009-10-13
seems like your nvidia drivers are not or not properly installed. If you go to system > adminstration > hardware drivers, what does it say? Which (if any) drivers are enabled?

---

