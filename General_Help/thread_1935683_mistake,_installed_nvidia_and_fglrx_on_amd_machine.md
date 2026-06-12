---
title: "mistake, installed nvidia and fglrx on amd machine"
date: 2012-03-04
forum: General Help
---

### Post by edvk on 2012-03-04
Hello,
I use ubuntu since years and never had a great problem, but i use it not study it.

I had been away for a while and had just changed from an Nvidia to an amd chipped computer. i had not realized this and when i logged into the machine the display was in a very strange mode somehow, still unclear why, when I left it was working fine. I wanted to fix this and mistakingly tried to install nvidia-settings.
since then i cannot boot whatever parameter i give, and even the livecd does not work. The screen always turns off at some stage.
i also cannot start up in console mode using ctr alt F1, same thing applies, screen goes.

i used the windows 7 ( i have double booter) and ext2read to get some logfiles:
kern.log says:
atombios stuck in loop more than 5 times
atombios failed  executing E262
clock recovery failed

jockey.log:
could not find module wl, ath-pci, vmxnet, fglrx-update and lots of nvidiastuff.

so I need to be able to  get into ubuntu (11.10) or at least some form of linux so that i might try to remove the nvidia stuff and take it from there.

thanks for any help.

ed van kuipers

---

### Post by dcstar on 2012-03-06
> **edvk said:**
> Hello,
I use ubuntu since years and never had a great problem, but i use it not study it.

I had been away for a while and had just changed from an Nvidia to an amd chipped computer. i had not realized this and when i logged into the machine the display was in a very strange mode somehow, still unclear why, when I left it was working fine. I wanted to fix this and mistakingly tried to install nvidia-settings.
since then i cannot boot whatever parameter i give, and even the livecd does not work. The screen always turns off at some stage.
i also cannot start up in console mode using ctr alt F1, same thing applies, screen goes.

i used the windows 7 ( i have double booter) and ext2read to get some logfiles:
kern.log says:
atombios stuck in loop more than 5 times
atombios failed  executing E262
clock recovery failed

jockey.log:
could not find module wl, ath-pci, vmxnet, fglrx-update and lots of nvidiastuff.

so I need to be able to  get into ubuntu (11.10) or at least some form of linux so that i might try to remove the nvidia stuff and take it from there.

thanks for any help.

ed van kuipers

Replace/remove the /etc/X11/xorg.conf file. Do a forum search for detailed instructions.

---

