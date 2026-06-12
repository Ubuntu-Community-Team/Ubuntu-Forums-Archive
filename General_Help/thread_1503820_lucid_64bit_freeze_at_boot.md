---
title: "lucid 64bit freeze at boot"
date: 2010-06-07
forum: General Help
---

### Post by vonkad on 2010-06-07
Dear all,

my acer 5510 extensa has stopped booting unexpectedly yesterday night. The boot process (with or without 'quiet splash') stops with 

fsck from util-linux-ng 2.17.2
/dev/sda1: clean 458237/4276224 files, 13719345/17089135 blocks

and never (yes, i have waited for hours) comes to life again. There are two partitions on the system /dev/sda1 (mounted as /) and /dev/sda5 as swap. /dev/sda3 is a win7 partition, which is not mounted at boot time.

I have booted into the live cd, chrooted and tried to fix packages (all ok) and to e2fcsk the disk (all ok, with all the strange parameters to e2fcsk).

There is no output whatsoever to log files. I can get to (initramfs) with break=init kernel parameter. The mode switches to graphics before the freeze, but enforcing vesa and stuff does not make any difference. The win7 boots ok. Please ask for any other information, i'm at the end of my (limited) wits ,,,

Thanks for any help with debugging this ...

Best Regards,
David Vonka

---

### Post by cwant on 2010-06-09
Just wanted to say that I have the exact same problem after a dist-upgrade yesterday. I tried modifying my fstab so there were no disk checks at boot, and still the thing just hangs at boot. I have no idea how to debug this.

Regards,
Chris

---

### Post by darkdragn on 2010-06-09
You have done about everything that I can think of... and taught me something i didn't know (really? break=init... i have to try it!!! ^_^) The only other thing could be... idk... if it freezes at graphics... do you have a special graphics card, with certain drivers that the update might have broken... >_<... i'm sorry i wich i could be of more help... (Thanks again for the break=init thing, ^_^)

Edit: The only other thing... Chris said (hehehe, that's my name too) that it happened to him after a dist-upgrade... Have you tried loading your old kernel, see if it's an issue with the new kernel... or the new kernel functioning with your graphics card drivers... >_<

---

### Post by cwant on 2010-06-10
I've tried a lot of things and have complete killed (and resurrected again) my machine, but I think the thing that finally got my machine back up and booting normally again is adding 

dev /dev tmpfs rw 0 0 
 
to /etc/fstab, as recommended in this thread:

[http://www.linode.com/forums/viewtopic.php?p=28115](http://www.linode.com/forums/viewtopic.php?p=28115)

Hope it helps!

Chris

P.S. Thanks for the tip darkdragn, but the same error occured when rebooting to a different kernel.

---

