---
title: "New driver breaks X / Can't get working shell to uninstall"
date: 2010-12-23
forum: General Help
---

### Post by fiddler616 on 2010-12-23
I was trying to get an extended desktop (with dual monitors) working on my Thinkpad T40 running Crunchbang 9.04 (Jaunty - GNOME + Openbox). Someone recommended trying the fglrx driver, which I installed. Upon rebooting, X was completely broken--it displayed a corrupted version of about 80% of my desktop. I tried switching to tty1, and then I got a very corrupted, tiled version of the splash screen shown while booting.

So I realized I had to uninstall the driver, which I thought I'd accomplish using aptitude at a bash prompt. So I booted into Recovery Mode, and selected the "Drop into root shell prompt" option. It asked for a root password. I never made a root account. Ubuntu doesn't *have* a root account by default. There is no root password, and sure enough--everything I tried was no good.

I did some more research, and discovered that most people don't get prompted for a password. Very mysterious.

Anyway, I discovered that I could append "init=/bin/bash" to a boot line in GRUB to get a bash prompt. Brilliant. It worked. Except the filesystem was mounted as read-only, which meant that both passwd and aptitude threw errors when I tried to use them. And my shell-fu isn't strong enough to gain write access to the hard drive.

For what it's worth, I have a different version of Crunchbang installed on the same computer (which can presumably access the files on the broken one) and I can also boot into any LiveCD image you want.

So...what do I do? Thanks in advance.

---

### Post by bwhite82 on 2010-12-23
I would boot into a live cd, mount the HD of the broken installation, open /etc/X11/xorg.conf and change:

Driver "fglrx"

to

Driver "vesa"

Reboot and then install a different driver once logged back in.

Make sure you're editing the xorg.conf of the HD and not the live CD, thus it would be in location like this:

/media/HARDDRIVENAME/etc/X11

---

### Post by fiddler616 on 2010-12-23
> **Soldierboy said:**
> I would boot into a live cd, mount the HD of the broken installation, open /etc/X11/xorg.conf and change:

Driver "fglrx"

to

Driver "vesa"

Reboot and then install a different driver once logged back in.

Make sure you're editing the xorg.conf of the HD and not the live CD, thus it would be in location like this:

/media/HARDDRIVENAME/etc/X11

Thanks, but I actually solved it a different way. I changed one of the parameters in GRUB, adding "text", and got a real, non-root bash prompt from which I could uninstall the driver.

---

