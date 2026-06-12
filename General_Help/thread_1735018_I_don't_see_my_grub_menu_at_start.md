---
title: "I don't see my grub menu at start"
date: 2011-04-20
forum: General Help
---

### Post by winchendonsprings on 2011-04-20
I don't see grub at start. I have grub-pc installed.

Ubuntu is the only OS installed on this machine.

I don't have a /etc/boot/grub/menu.lst or a /boot/grub/menu.lst file either.

What's going on?

10.10 64bits

---

### Post by wolfen69 on 2011-04-20
With only 1 OS on the computer, you will not see grub unless you hold shift key during boot.

---

### Post by drs305 on 2011-04-20
You are using Grub2, which uses a different configuration file: /boot/grub/grub.cfg.

Grub2 doesn't display the menu if you have only one OS. The thinking was to speed up the boot. If you want to display the menu during boot, hold down the SHIFT key and it should appear.

If you always want it to appear, you will have to edit one of the system files:
```
gksu gedit /etc/default/grub
```

Place a # symbol on this line.
> #GRUB_HIDDEN_TIMEOUT=0

Then run this to update the menu.
```
sudo update-grub
```
To get an introduction on how Grub2 works, you can take a look at "Basics" and "Tasks" in my signature line,

---

### Post by ImDougy on 2011-04-20
when i installed ubuntu as the only os on my computer i didn't get a grub menu either. since it's the only os on the computer it skips the menu and boots the os. with the windows bootloader u press F8 to force it to show the boot menu, so there could be a key to show the grub menu, only problem is i don't know what key or if there is even a key to do this.

---

### Post by winchendonsprings on 2011-04-20
Thank you all. Marked solved.

---

### Post by wolfen69 on 2011-04-20
> **ImDougy said:**
> only problem is i don't know what key or if there is even a key to do this.

Read the 2 posts above you.

---

