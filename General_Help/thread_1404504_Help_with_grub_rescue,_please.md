---
title: "Help with grub rescue, please"
date: 2010-02-11
forum: General Help
---

### Post by ratcheer on 2010-02-11
Ok, I screwed up, deleted my Lucid Alpha partitions, and forgot to run update-grub. So, now my system boots up to a grub rescue prompt.

I have researched how to use it at [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) and everything goes great until I "insmod /boot/grub/linux.mod" It gives an error saying "symbol grub_getcharwidth not found".

So, to make sure everything else is correct, I ran "ls /boot" and it does show me all the kernels on the drive I am trying to boot to. It looks like everything is right until the insmod command errors.

So, I need some emergency help, please.

Yim

---

### Post by ratcheer on 2010-02-11
Well, not exactly solved, but worked around. If there are easy and hard ways to fix a problem, I usually pick the hard way. Heh, heh. I reinstalled the Lucid Alpha, which updated grub. Then, I booted back to Karmic, deleted the Lucid partitions, again, and made certain to run update-grub, again. Back in business.

Tim

---

### Post by mahboop on 2010-05-14
> **ratcheer said:**
> Well, not exactly solved, but worked around. If there are easy and hard ways to fix a problem, I usually pick the hard way. Heh, heh. I reinstalled the Lucid Alpha, which updated grub. Then, I booted back to Karmic, deleted the Lucid partitions, again, and made certain to run update-grub, again. Back in business.

Tim

if I reinstalled the whole system, my data will be deleted. I want to fix this problem only: [COLOR="DarkRed"]**error: the symbol "grub_getcharwidth" not found**[/COLOR]

any help?

---

