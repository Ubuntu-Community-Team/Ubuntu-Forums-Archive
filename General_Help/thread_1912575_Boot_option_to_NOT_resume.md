---
title: "Boot option to NOT resume?"
date: 2012-01-20
forum: General Help
---

### Post by Loco Ulysses on 2012-01-20
When my laptop hibernates, is there a way to choose NOT to resume, but just to start fresh? Is there a way to put this on the boot menu?

I ask, because my laptop takes FOREVER (~10 minutes) to resume from hibernate under Ubuntu, so I don't usually hibernate it intentionally, but it will if it runs out of power. I don't want to turn off hibernate because sometimes I AM doing something important and am glad it saved it. But most of the time I'd just like to start fresh.

This is particularly an issue right now because my battery is totally shot, so if the power plug pulls 1/4 of the way out for a few seconds without me noticing this thing hibernates (new battery is on the way).

So, in short, I have my reasons. Is there a way to make a boot option?

---

### Post by Toz on 2012-01-27
The kernel boot option **noresume** should do this for you. 

You can either add it directly to the grub boot line when booting ([https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot")) or make it permanent by adding it to /etc/default/grub and running:
```
sudo update-grub
```
...([https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2]("https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2")).

---

### Post by Loco Ulysses on 2012-01-27
Thanks Toz! So simple, wonder why it never came up in all my googling "grub don't resume" etc. Doesn't seem to be anywhere on the page you linked to either. Thanks again.

---

### Post by drs305 on 2012-01-27
> **Loco Ulysses said:**
> Thanks Toz! So simple, wonder why it never came up in all my googling "grub don't resume" etc. Doesn't seem to be anywhere on the page you linked to either. Thanks again.

It's not on the Grub 2 page because it is a kernel option and not really a Grub option. Kernel commands can be passed by the 'linux' line in Grub 2 (such as *nomodeset* and *noapic*) but Grub is just the messenger and it is the kernel that acts on the opitons.

Here is a link to kernel options. I don't know how current it is:
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt]("http://www.kernel.org/doc/Documentation/kernel-parameters.txt")

---

