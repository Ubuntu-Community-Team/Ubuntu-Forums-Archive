---
title: "Can't boot my original hdd"
date: 2010-03-06
forum: General Help
---

### Post by larryx2 on 2010-03-06
I am in hopes that someone can help me with this problem and that all is not lost. Here is what happened:

I have a pc that has win xp for a long time now so last year wanted to try Ubuntu so I got another hdd and installed on it. 

Now the way it has been set up is I get a menu at boot and it would show Ubuntu 9.04 with all it's kernel updates over time, I would just scroll down and pick my xp and it would boot from xp...or what os I choose. 

This worked great for the past year or so and now I decided to install win 7 on the hdd that had Ubuntu 9.04 on and the install went fine. When I changed back to my orig hdd in the bios to boot my xp hdd I get an error:

Grub Loading stag1.5.
Grub Loading, Please wait...
Error 17

I am worried about this cause my xp has important stuff that I need...lol

Can this be fixed? Can I delete the grub all together somehow as I just can not figure out how to get back into my first xp hdd. My new windoz 7 boots fine when I set that hdd to boot in bios, not my xp hdd though.

I appreciate any help on this guys...thanks.

---

### Post by jack.herbert on 2010-03-06
Hi!
I don't really know how to fix grub but I know that by downloading/burning/booting with the super GRUB disk you should at least be able to boot in xp.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by larryx2 on 2010-03-06
> **jack.herbert said:**
> Hi!
I don't really know how to fix grub but I know that by downloading/burning/booting with the super GRUB disk you should at least be able to boot in xp.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Thanks jack, 
I got it figured out...lol
Wow, I'm quite happy and thanks for your help.
I just used my orig xp disk and entered recovery mode. You can
choose your drive and enter commands to help fix problems.
I used help from a list of cmds and "fixmbr" did the trick. Time for a 
beer now:D

Thanks again

---

