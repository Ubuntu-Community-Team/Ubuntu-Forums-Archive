---
title: "no symbol version for module_layout"
date: 2011-06-30
forum: General Help
---

### Post by dorfsmay on 2011-06-30
I'm trying to re-compile a kernel module, to add debug mode to it.

I did this:

cd /usr/src
apt-get install linux
ln -l linux-2.6.38 linux
cd linux
cp /boot/config-2.6.38-8-generic .config
make oldconfig
vi .config (to switch CONFIG_IWLWIFI_DEBUG=y)
make modules

I get a .ko file but when I modprobe it, I get:
iwlagn: no symbol version for module_layout

When I compare the output "modinfo" for the original and my new module, the diff is:
< vermagic:       2.6.38-8-generic SMP mod_unload modversions
> vermagic:       2.6.38.2 SMP mod_unload modversions

I got 2.6.38.8 from kernel.org, same thing. It does not matter what I do, I cannot get the version right, and alway get the same error message.

What am I doing wrong?

Thanks.

---

### Post by bjlg on 2011-07-08
I have the same  question !

---

