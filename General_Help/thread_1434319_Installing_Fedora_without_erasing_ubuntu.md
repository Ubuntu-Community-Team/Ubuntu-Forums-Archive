---
title: "Installing Fedora without erasing ubuntu?"
date: 2010-03-20
forum: General Help
---

### Post by karthick87 on 2010-03-20
I would like to try another flavor of linux (fedora)..Currently i am using Ubuntu 9.04, without erasing ubuntu i like to try Fedora..So can someone tell me how to install fedora without losing Ubuntu?

---

### Post by cottfcfan on 2010-03-20
If Ubuntu is taking up your whole disk, then when you install Fedora from the live CD, you should get an option to "install them side by side" or something similar.
 Choose this option and you`ll get a choice at boot of which OS to use.

---

### Post by darolu on 2010-03-20
It's good to try other distros, sometimes you find great stuff (after all that's how I discovered Ubuntu).

You can install Fedora and dual boot (or triple+ if you also have win) but for testing purposes I recommend using a Virtual Machine like Virtual Box; this way you can install and try Fedora within Ubuntu, no partitioning needed and it's safe.

Open Add/remove software (under applications menu) and search for Virtual Box, there are tons of tutorials, I'm sure you'll find a good one that teaches you how to install any distro (or win) using Virtual Box, just google for it.

If you want to hard-install it, it is pretty much the same procedure you followed with Ubuntu, Fedora also has a LiveCd, you re-partition with Gparted as well, etc. If you need more detailed instructions, you can follow guides like this one: [http://docs.fedoraproject.org/install-guide/f12/en-US/html/](http://docs.fedoraproject.org/install-guide/f12/en-US/html/)

---

### Post by karthick87 on 2010-03-20
I have some free space around 20 GB,so is it possible to have fedora on this free space?

---

### Post by cottfcfan on 2010-03-20
Yes. Shoudn`t be a problem.

---

### Post by karthick87 on 2010-03-20
After installing will i have any GRUB issues?

---

### Post by darolu on 2010-03-20
I don't think you'll have any, Fedore uses GRUB also; if you do get a problem with grub, you can always re-install it, follow the instructions in this link: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
It say "after windows" but works with "after fedora/other distro" also.
Again, if you want to play it safe, consider a virtual machine.

---

### Post by karthick87 on 2010-03-20
Okey thanks a lot i will give a try..

---

### Post by coffeecat on 2010-03-20
One thing to beware of with Fedora is that the only other OS the installer will pick up and automatically add to its grub menu is Windows! It disdainfully ignores any other Linux installations. Extraordinary. Every major Linux distro that I've tried in the last 3-4 years has happily added every OS it could find to its grub menu - but not Fedora.

So - if you install Fedora's grub to the mbr you'll get a (blue) menu for Fedora and Windows (if you have Windows). And you won't see it unless you press esc, because the "hiddenmenu" option is the default in grub's menu.lst. Oh, and Fedora 12 is still using legacy grub. You may need to reinstall Ubuntu's grub using the link darolu provided.

Fedora's a good distro to try out but it has a few of its own quirks. Its policy regarding non-free software is much stricter than Ubuntu, so if you want multimedia, proprietary drivers and other goodies here's a useful link:

[http://www.mjmwired.net/resources/](http://www.mjmwired.net/resources/)

And one thing that will probably throw you is the bizarre spatial mode that Nautilus defaults to. I think there must only be two human beings in the whole known universe who like spatial mode: the lead gnome dev for nautilus and the Fedora gnome maintainer. Nevertheless, you get it dumped on you. The fix is simple - it's somewhere in the Nautilus menu Edit > Preferences. You'll probably want browser mode.

---

