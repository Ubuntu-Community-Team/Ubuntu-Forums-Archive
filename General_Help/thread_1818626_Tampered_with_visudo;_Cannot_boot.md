---
title: "Tampered with visudo; Cannot boot"
date: 2011-08-05
forum: General Help
---

### Post by battery2004 on 2011-08-05
Hello,

So to get to the point.

Right now I`m on LiveCD. When I tried to boot up the laptop it showed "Please append a correct "root=" boot option.

As I recall I added a line to Visudo sudoers list. And seems that, that could cause the problem. (But i might as well, have done something else)

What would be the next step?


// Running Ubuntu 11.04

---

### Post by Beacon11 on 2011-08-05
> **battery2004 said:**
> As I recall I added a line to Visudo sudoers list. And seems that, that could cause the problem. (But i might as well, have done something else)

Well, what did you add? Also, are you able to mount your root partition using the LiveCD? Has its UUID or partition number changed?

---

### Post by galvatron408 on 2011-08-05
sounds like you messed up your grub.cfg

but, the good news is, it is really easy to fix.

While you're on the machine with that LiveCD, run "sudo grub-mkconfig"

grub-mkconfig will regenerate your grub.cfg for you.

---

