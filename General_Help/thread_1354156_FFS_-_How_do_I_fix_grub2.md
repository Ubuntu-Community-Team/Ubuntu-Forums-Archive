---
title: "FFS - How do I fix grub2?"
date: 2009-12-13
forum: General Help
---

### Post by detroit/zero on 2009-12-13
Not sure what happened. I had some updates come through last night or today, and I think one of them was for grub.

In any event, I'm suddenly unable to access any of my Ubuntu kernels. Whenever I try to load anything from the grub menu, I get a message, "you need to load the kernel first".

Berlios is offline or overloaded or something, because I can't download the supergrubdisk1.21 to save my life. I can't update-grub or grub-mkconfig because for some reason I can't chroot from a livecd (can't find device for '/').

I'd really rather not go through the three or four hours it's going to take to re-install Ubuntu and track down and re-install all my software and such over a bootloader.

Any suggestions?

---

### Post by detroit/zero on 2009-12-13
I managed to get it.

For future reference, at the grub prompt:
```

ls -l (hd0,[COLOR=Red]X[/COLOR])/    #(find your boot and root partitions)
set root=(hd0,[COLOR=Red]X[/COLOR])    #(set the boot partition)
linux /vmlinuz-2.6.31-[COLOR=Red]XX[/COLOR]-generic root=/dev/sd[COLOR=Red]X[/COLOR]/[COLOR=Red]X[/COLOR] ro quiet splash
initrd /initrd.img-2.6.31-[COLOR=Red]XX[/COLOR]-generic
boot
```And once inside your system, many hours later, open a terminal and:
```
sudo update-grub2
```Two - going on three - hours after I rebooted after an update that made changes to grub.

Why is it that the bootloader doesn't fix itself after it's updated? Who's the genius who decided to put a beta-quality bootloader in the finished, final-release version of an OS? Why, so very close to the year 2010, am I still configuring my bootloader by hand like it's 1985?

Sickening.

I hate you, Ubuntu.

---

### Post by Technical on 2010-03-10
> **detroit/zero said:**
> I managed to get it.
Who's the genius who decided to put a beta-quality bootloader in the finished, final-release version of an OS? Why, so very close to the year 2010, am I still configuring my bootloader by hand like it's 1985?
I'm really disapointed also.
I can't go further booting. Can't correct anything...

---

