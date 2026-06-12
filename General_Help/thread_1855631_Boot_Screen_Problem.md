---
title: "Boot Screen Problem"
date: 2011-10-06
forum: General Help
---

### Post by Nosophorus on 2011-10-06
Hi!

I followed [this tutorial]("http://maketecheasier.com/turn-ubuntu-lucid-mac-os-x/2010/06/01") to turn the appearance of my Ubuntu (Lucid Lynx) into a Mac OS X. Then I created another account on my machine just to test that in order not to mess my original configurations on my old account.

After doing everything as stated on that tutorial, I ran the uninstaller and deleted the new account I created for the test. There were no problems at all after the uninstall, except that the boot screen is the Apple logo and not the [Ubuntu logo]("http://freakytech.files.wordpress.com/2010/06/boot.png").

What should I do to put back on the boot screen the good old Ubuntu Lucid Lynx logo?

Every time I boot or turn off my computer the Apple logo appears on the boot screen/turn-off screen.

Many thanks in advance!

Nosophorus

---

### Post by Nosophorus on 2011-10-06
Hi!

I solved the problem!

I went to /lib/plymouth/themes and deleted the Mac OS X theme, then I ran these commands:

sudo update-alternatives --config default.plymouth
sudo update-initramfs -u
sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth 100
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u

That's it!

See You!

Nosophorus

---

