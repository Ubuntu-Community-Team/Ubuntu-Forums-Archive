---
title: "Tired of outdated documentation and in need of help"
date: 2010-05-30
forum: General Help
---

### Post by Musicologynut85 on 2010-05-30
Hello,

I installed Lucid (clean install after several attempts at upgrading from Karmic failed), and I have an Intel 8xx video card. I was able to get Lucid installed by adding "xforcevesa" into the command line at startup.

Now I would like to try changing my computer away from Vesa and seeing if I can try to get the i915 driver working.

That being said, I cannot figure out where to go to change my kernel boot configurations. Every tutorial I've found refers me to /boot/grub/menu.lst which I cannot find. Ever since I moved from Karmic to Lucid, I've regretted it as it seems like all the How-To documentation is no longer valid, everything has been changed and moved around.

I don't know why it is dumping me onto Vesa, or why my stupid driver was blacklisted; everything was working fine under Hardy, Jaunty, and Karmic. Why problems now?

Does anyone know how I can get into my boot setings and replace "xforcevesa" with something that will make the intel driver work?

---

### Post by dcstar on 2010-05-30
> **Musicologynut85 said:**
> He
.........
Does anyone know how I can get into my boot setings and replace "xforcevesa" with something that will make the intel driver work?

You search for a Grub2 HOWTO and stop looking at obsolete legacy Grub documentation.

---

### Post by Rubi1200 on 2010-05-30
Hi,
I think this might be what you are looking for:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by Musicologynut85 on 2010-05-31
I found a different work-around downloading some packages off someone's PPA (dedicated to my make of computer).

Thanks for the help though. I'm not sure what the difference is between "Legacy" and "Grub2." Also, the Grub loading screen is really short...

It is working fine now...

---

