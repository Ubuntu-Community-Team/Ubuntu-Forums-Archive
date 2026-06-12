---
title: "How to use only one of two graphics cards?"
date: 2011-05-09
forum: General Help
---

### Post by Tom Perry on 2011-05-09
After much research and general mucking around, I have decided to ask you fine gentlemen (and ladies!) for help.

My situation is like so: I have two NVIDIA GTX 460 graphics cards running the latest (260.19.06) proprietary drivers. I SLI these together under Windows 7 for gaming. However, for day to day usage I have Ubuntu 10.1 running on my two monitors using twinview.

My problem is that the xserver refuses to load (I get the "screens found, but none have a usable configuration" error) when both my graphics cards are plugged in and powered; if I remove the power to one, the system works fine. If I was just using Ubuntu, I would simply leave one unplugged but, because I'm not, its a pain to have to plug/unplug one every time I want to switch operating system.

I have tried every modification to the xorg.conf file that I can think of and a few more found in the documentation and via google, all to no avail. I have also tried everything again with twinview disabled and only one monitor plugged in.

I am aware that SLI isn't compatible with twinview, I don't really need to use it, although it would, of course, be nice.

The most obvious solution I can think of is to somehow prevent Ubuntu from adding the second graphics card as a device, before it tries to start the xserver. Any hints of how to do this, or other suggestions, would be greatly appreciated. :)

---

### Post by dino99 on 2011-05-09
[http://ubuntuforums.org/showpost.php?p=10060072&postcount=2](http://ubuntuforums.org/showpost.php?p=10060072&postcount=2)

note: as the kernel directly deal with X now, xorg.conf often conflict if tweated, try without it:

sudo rm /etc/X11/xorg.conf

from synaptic:
- remove/purge ALL the installed nvidia packages
- reinstall: nvidia-current, nvidia-common, nvidia-settings
- check that dkms is installed too

---

### Post by Tom Perry on 2011-05-09
Cheers dino, I'll give that a go.

---

### Post by Tom Perry on 2011-05-13
Nope, I tried what you suggested and I still get the same error AND I have to change my monitor settings every time I boot because without an X config file they are lost.

Any other suggestions?

---

