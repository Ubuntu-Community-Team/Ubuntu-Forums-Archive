---
title: "NVidia problems after system upgrade"
date: 2010-05-06
forum: General Help
---

### Post by GNUinU on 2010-05-06
Hey everyone.
I wanna begin saying my Linux level is below 0 in a 0-10 scale. (OK... not that much... but I'm such a noob).

I start the system up (10.04 64bit) and it tells me there are some new upgrades, including something called linux-image-2.6.32-22-generic (I think), what I assume is a kernel update.

After downloading and installing them, I reboot the system as required and select the new kernel in the grub. Before loading the system, it shows some errors messages including "Failed to load the NVIDIA kernel module!" and some other stuff about my graphics.

There are some options, like re-configuring the xorg file, starting up in a lower screen resolution, and so on...

I try some of those options, but none seem to work, so I restart and select the kernel 21 in the grub. Everything loads OK, so I decide to delete "kernel 22" and keep using the older one.

I guess there's something I'm not doing, a missing step I should take, but googled a bit and found nothing.

Talked to a friend of mine about this, and told me I should compile my NVidia driver again using the new kernel (or something like that). He doesn't own an NVidia card so can't tell me how to do it, and I didn't even know that was an option, so...

Can anyone give me a hand with this?


Thanks!!

---

### Post by dabl on 2010-05-06
This might help:

[http://kubuntuforums.net/forums/index.php?topic=3107406.0](http://kubuntuforums.net/forums/index.php?topic=3107406.0)

Don't worry about the "Kubuntu" aspect -- just use gedit instead of kate, and "gdm" instead of "kdm".  Everything else is the same.

---

### Post by Chemist69 on 2010-05-06
Hi, I had the same problem of the broken driver after the kernel upgrade.

This is what fixed it for me:
Start Applications > System > Hardware drivers
Remove the activated nvidia driver
Reinstall / Reactivate it.

After the required reboot, the driver was back again fine.

Good luck.

---

### Post by GNUinU on 2010-05-07
Thanks guys!
Will try it out as soon as I get back to my laptop again, as it's the one with an NVidia card. =)

---

