---
title: "Nvidia/Intel Optimus and video drivers"
date: 2010-11-03
forum: General Help
---

### Post by thehero on 2010-11-03
I have a Thinkpad T410s with Nvidia/Intel Optimus technology. In the hardware bios I have the ability to turn off Optimus and use discrete (Nvidia) or integrated (Intel) graphics. 

What I'm trying to figure out is how to disable the Nvidia proprietary driver without uninstalling it. I want to be able to choose an option in the bios (discrete/integrated) then boot into the OS without uninstalling a package to make X work. I know I may have to change xorg.conf to use the nvidia driver but that's easy enough.

Is it possible to disable the Nvidia driver with a kernel argument? If not can I blacklist it? With the Nvidia driver installed it stops the Intel driver from loading correctly. 

Thanks for any help or ideas...

---

### Post by cwwilson721 on 2010-11-03
Disable/remove the Nvidia driver via System > Administration >Additional Driver. Then reboot. You'll be in Nouveau mode.
After that, try your bios change, see what happens.

IIRC, that should do what you want

---

### Post by P4man on 2010-11-03
That will probably do if you dont want proprietary drivers when using the nvidia card (which for the most part, defeats the purpose of enabling the nvidia card, since 3d performance of nouveau isnt exactly stellar).

Unless you can re-enable the nvidia drivers without internet connection (which I think is the point of the OP) after an initial install. And I have no idea if that works. At the very least it will require another reboot.

---

### Post by thehero on 2010-11-03
P4man is correct.

I just wanted to clarify a little what I'm trying to do.

Basically what I'm wondering is how to disable the Nvidia proprietary driver without uninstalling it? Possibly with a argument in grub or something being blacklisted. Rebooting is not a concern.

---

### Post by P4man on 2010-11-03
If you disable them in jockey ("additional drivers") I dont think they are actually removed from the harddisk. But Im not entirely certain if jockey will propose to install them if you are not online. I suggest you give it try. 

If it doesnt work, see if you can do anything with

```
jockey-text
```

to reanable the nvidia drivers offline. use 

```
jockey-text -h
``` to see the help.

If jockey cant do it, apt-get might do it, and use the cached files even offline. not entirely sure about the correct packages but something like

```
sudo apt-get install nvidia-current
```

You may also need to run 

```
sudo nvidia-xconfig
```

and possibly you need to blacklist the nouveau drivers.

Anyway, that is just a possible and clumsy solution, I sure hope there is an easier way.

---

