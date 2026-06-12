---
title: "Dual Boot Windows &amp; Ubuntu through BURG?"
date: 2010-12-30
forum: General Help
---

### Post by jvacek996 on 2010-12-30
I have a Dualboot already set up through lilo, and then when i choose Ubuntu, Grub pops up and i can choose between different kernels and some old windows loaders, everything is working fine.
But is it possible to instrall BURG in a way that i can skip the lilo AND grub and directly boot into either Windows 7 or Ubuntu straight away, from a nice and colorful bootloader, or is it just impossible? Just asking, if it's not possible, then i'll just forget it.

Thanks a lot!

---

### Post by dcstar on 2010-12-31
> **jvacek996 said:**
> I have a Dualboot already set up through lilo, and then when i choose Ubuntu, Grub pops up and i can choose between different kernels and some old windows loaders, everything is working fine.
But is it possible to instrall BURG in a way that i can skip the lilo AND grub and directly boot into either Windows 7 or Ubuntu straight away, from a nice and colorful bootloader, or is it just impossible? Just asking, if it's not possible, then i'll just forget it.

Thanks a lot!

Yes.

Lilo just duplicates what Burg/Grub does, so it is pretty pointless having it.

---

### Post by Rubi1200 on 2010-12-31
As above, yes EXCEPT if this is a Wubi install, in which case the answer is no because you will break it.

---

### Post by jvacek996 on 2010-12-31
> **Rubi1200 said:**
> As above, yes EXCEPT if this is a Wubi install, in which case the answer is no because you will break it.

Nope, I'm not on a Wubi Install, I used to have that but then realised that ubuntu is worth shrinking my Windows Partition.
My W7 is on /dev/sda1 and Ubuntu on /dev/sda4 if that clarifies it.

If there is anyone who could write me a command for terminal i would be very, very happy coz i am kind of a n00B when it comes to Linux, and i already managed to delete both of my bottloaders once.

Happy New Year by the way.

---

### Post by dcstar on 2010-12-31
> **jvacek996 said:**
> Nope, I'm not on a Wubi Install, I used to have that but then realised that ubuntu is worth shrinking my Windows Partition.
My W7 is on /dev/sda1 and Ubuntu on /dev/sda4 if that clarifies it.

If there is anyone who could write me a command for terminal i would be very, very happy coz i am kind of a n00B when it comes to Linux, and i already managed to delete both of my bottloaders once.

Happy New Year by the way.
This will show you how to install Grub, then you can boot Ubuntu and replace it with Burg:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by jvacek996 on 2011-01-01
> **dcstar said:**
> This will show you how to install Grub, then you can boot Ubuntu and replace it with Burg:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I actually managed to install burg and get rid of grub and configured lilo not to show up at all which basically leaves me with what I intended to do.

I was just scared about doing the whole thing because when I tried to run sudo burg-install /dev/sda it told me that it is a bad idea, and that's why i asked the forum about it, but it turns out that when i used my jedi --force everything worked just fine. I still have a few bugs with it, but I will make a new thread since it is a bit off-topic.

Thanks for the help anyway, hope this helps anyone else in the future as well

---

