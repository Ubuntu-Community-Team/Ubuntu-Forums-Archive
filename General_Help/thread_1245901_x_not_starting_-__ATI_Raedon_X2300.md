---
title: "x not starting - :\ ATI Raedon X2300"
date: 2009-08-21
forum: General Help
---

### Post by timClicks on 2009-08-21
Hi all,

I've come accross a fairly serious error. My laptop will no longer start X. Xorg.0.log attached.

Am running Ubuntu 8.10, ATI Raedon X2300 graphics card with drivers installed from ATI website. From looking through some of the web posts, it seems that there's a conflict between the different drivers.

Ideally, I would like to use apt-get to remove the incompatible device drivers. Am scared to use apt-get remove because I don't know how to connect to the Internet via CLI. Plus, as I've compiled the driver myself, I don't know if apt-get would know what to do.

Is it possible to upgrade the distro using a Alt CD (mounted iso on a USB) without needing gtsu "media/cdrom/cdromupgrade"? I have tried running a 9.04 Live CD to get things working, but the cdromupgrade script thinks that I'm running the most recent release.

Any advice would be great.

---

### Post by timClicks on 2009-08-21
Managed to get X11 working. Copied an old version of xorg.conf to xorg.conf.

Now the login manager doesn't start and it does straight to LXDE - even though I'm sure I have GNOME as default, but that may be because I'm already logged in as a user. At least something works though. Phew.

---

### Post by timClicks on 2009-08-27
Sorted. Once LXDE had started I was able to d/l an alt installer and upgrade.

---

