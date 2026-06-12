---
title: "kernel won't boot: can I find out why not?"
date: 2012-05-13
forum: General Help
---

### Post by Toon81 on 2012-05-13
Hi all,

I am currently running Lubuntu 12.04. I have installed the linux-lowlatency package from the repos; it's the one that according to the package, always depends on the latest one. Right now that's 3.0.2-23.31, according to Synaptic. I also have a real-time kernel installed, a similar version. Don't get me wrong: that one is not from an official PPA, and I'm not in any way suggesting that anyone help me with that one.

I also have the regular generic one installed, version 3.20-24.37. When I start my PC up and choose the low-latency kernel or the real-time kernel from the GRUB menu, the screen stays black. When I choose the regular one, my Lubuntu installation boots up like a charm. I'm concluding that something about those kernels is causing my system to hang, and it's likely to be something they have in common (which is why I mentioned the real-time one).

Now my question is: what happened to those text messages Linux systems used to scroll across the screen during startup? I know they're still out there because I've seen them in other recent distros. How can I turn those back on, so I can write down and Google whatever message is on the screen when the kernel hangs? Is there any way to check logs? I already turned the "No" in /etc/default/bootlogd to a "Yes" but /var/log/boot remains empty. There's a /var/log/boot.log but that only seems to show the last successful boot, which is nice, but not very helpful.

Any tips on how I can go about investigating the problem? If you've got an awesome tip to actually solve it, that would also be welcome, but I'm fine with doing some more research on my own.

Thanks in advance for pointing me in the right direction! :)

---

### Post by Toon81 on 2012-05-15
*Nobody* on the official Ubuntu forum can point me to the kernel logs?

---

### Post by oldos2er on 2012-05-15
To see text on booting, edit /etc/default/grub and change the line 

GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"

to

GRUB_CMDLINE_LINUX_DEFAULT="text"

Then run ```
sudo update-grub
``` and reboot.

---

