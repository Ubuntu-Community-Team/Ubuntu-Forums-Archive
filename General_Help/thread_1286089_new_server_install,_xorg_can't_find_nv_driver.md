---
title: "new server install, xorg can't find nv driver"
date: 2009-10-08
forum: General Help
---

### Post by phyxion on 2009-10-08
Hi all, I've been using Debian for a server at work for a couple years now and it's been working great, aside from having no X on it. (Not related but I'm familiar with apt-get and dselect, etc).

I recently set up a desktop machine using Ubuntu 9.04 server disk (I like to keep things lean, and this is a dev box), figuring I could get X up and running afterwards. I was wrong. This box has an onboard Nvidia 6150SE graphics card. I've installed nvidia-glx-71 and xorg 1.6.0 (and I think gdm as well), but I still can't get X to start. The error message says (EE) Failed to load module "nv" (module does not exist, 0) (EE) No drivers available.

lsmod shows this line: agpgart     42696  1 nvidia (and dmesg shows the Nvidia kernel module being loaded with no errors).

I was getting a DKLM (?) message earlier but installing the kernel 2.6.28-15-server sources fixed that.

Also, of course, xorg.conf is empty. What else am I missing? (Also, if possible, I'm looking for a solution that will continue booting to console, and let me start X when I need it, which is not always)

Thanks :)

Edit: Mostly solved. I did sudo apt-get install nvidia-glx-180, then rebooted, and got the GDM X login with a single terminal window. Installed fluxbox and got that working. Still don't know how to have it boot into console normally and only load X when I want. I'll keep looking.

---

