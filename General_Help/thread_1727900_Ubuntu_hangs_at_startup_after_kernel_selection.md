---
title: "Ubuntu hangs at startup after kernel selection"
date: 2011-04-13
forum: General Help
---

### Post by gofurygo on 2011-04-13
Hello

Recently I experience some odd issue with Ubuntu 10.10. Maybe its behaviour is result of an update, Im not sure.

Lately, every once in a while, Ubuntu hangs at start up. Im running 10.10 from a wubi installation - without any problems since. Now, I select the kernel, do ENTER, then I get the blinking big dos-like cursor (still normal)...but when it should show the list of "checks"... ( I dont know how this is called... where it checks services, battery state and comments everything with [OK]) it suddenly hangs. All I get is a small blinking cursor, but not more. I need to power down and turn my computer on again, then it usually works...

Does anybody have an idea whats wrong there? Was there a grub update?... 

Hope you guys can help me out...

Fury

---

### Post by Rubi1200 on 2011-04-13
What graphics card do you have installed?

---

### Post by gofurygo on 2011-04-13
Hi

Its an onboard graphic card on my notebook:
Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller

The thing is, it worked without _any_ problems until a few days ago... but lately it hangs, sometimes...

Cheers

---

### Post by Rubi1200 on 2011-04-13
Do you have Compiz enabled?

I recommend turning it off for the moment to see if that is a possible source of the problem.

You can try this the next time you start the computer:

when you select Ubuntu press "e" to edit the highlighted kernel. Navigate using the arrow keys and find the line that ends with quiet splash.

Add the following parameter, i915.modeset=1, so it looks like this:

> quiet splash i915.modeset=1 (notice the space after splash)

Then, "Ctrl" + "x" to boot.

If it helps, we can make this more permanent.

---

### Post by gofurygo on 2011-04-21
Sorry for my late reply. I was kinda busy lately.

I think I found the reason for the "hanging". It seems, that this behaviour is somehow connected to my wlan turned on/off at boot time. When I start my notebook with the WLAN switch turned on, I have a good chance that it hangs on boot-up. 

When I power down, turn off the WLAN switch, boot it back up I most likely end up with the login prompt.

Can this be "the" reason? I remember, when I installed ubuntu, I had the wireless switch turned off...

On a side note, is it just me, or has Ubuntu became awfully slow after the latest series of updates? Normally, I logged on and bang, gnome desktop was there... now it takes almost 10 seconds until I see my desktop although I didnt add/remove any significant amount of files/software..  :( alot of harddrive activity though

Thanks in advance...

Fury

---

