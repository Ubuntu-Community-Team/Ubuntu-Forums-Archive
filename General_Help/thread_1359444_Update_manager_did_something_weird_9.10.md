---
title: "Update manager did something weird 9.10"
date: 2009-12-19
forum: General Help
---

### Post by alex_dc on 2009-12-19
I ran update manager last night, and today, when I went to boot my system, Grub asked me if I wanted to boot to: Ubuntu 2.6.31-14, 2.6.31-15, or 2.6.31-16.

I didn't make any other system changes/install any other software last night, and this problem has never come up before. I would include more information, but I honestly don't know what could be related to this.

Ideas?

---

### Post by Darael on 2009-12-19
The grub menu, which was set to hidden before, is now ignoring that part of its config file - a few people have found this recently. It should autoload the most recent after 10 seconds if you just leave it. I'm sure it'll be fixed soon!

---

### Post by alex_dc on 2009-12-19
But why would it ask me to choose between different "versions" of Ubuntu?

Also, is there anyway to manually change the configuration? I tried a quick Google search, but couldn't find much about the set up of Grub 2.

---

### Post by HappyFeet on 2009-12-19
What happened is normal. There was a kernel update and it will always give you the choice to boot to a previous kernel if the new one is not working well for you. I would not worry about this. It is not giving you a choice of ubuntu versions, but rather different kernels. But it is still the same version of ubuntu. This happens on all installs of ubuntu.

---

### Post by alex_dc on 2009-12-19
> **HappyFeet said:**
> What happened is normal. There was a kernel update and it will always give you the choice to boot to a previous kernel if the new one is not working well for you. I would not worry about this. It is not giving you a choice of ubuntu versions, but rather different kernels. But it is still the same version of ubuntu. This happens on all installs of ubuntu.
 
Sorry, it is the kernel. I only gave it a passing glance.
 
That still begs the question of why I have a choice between loading THREE different kernels. Also, I understand this is 'normal', I wasn't asking that. I was asking how to manually configure the bootloader so it won't bring up the prompt every time I boot my machine.

---

