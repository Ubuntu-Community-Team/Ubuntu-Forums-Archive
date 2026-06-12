---
title: "Boot into Memtest86"
date: 2010-04-18
forum: General Help
---

### Post by algebralives on 2010-04-18
I have an Acer AspireOne netbook running Netbook Remix (9.10). I fiddled with my Grub configs and now I only boot into Memtest.

I've read the other forum posts. I know what I should do:

[LIST=1]
[*]Create a live USB.
[*]Change my BIOS order to boot from the USB.
[*]Reinstall GRUB from LiveUSB
[/LIST]
The problem is: I've done that. I can't boot from my USB for some reason. It still keeps running Memtest. What's going on?

---

### Post by quixote on 2010-04-19
Grub does have its own command line that you can use to try to fix things.  Since you have no way of external booting that works, that may be the way to go.  [https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

Do you get a grub menu at all?  Even if all it says is memtest.  Or does it just boot straight into memtest?

---

### Post by drs305 on 2010-04-19
algebralives,

Welcome to Ubuntu and the Ubuntu forums.  :-)

If you are using Grub 2, does holding down the SHIFT key during the early stages of the boot display the Grub menu?

You may see your other options and be able to boot one of the normal kernels from there. If so, once you get to the Desktop we can help you restore the default OS.

---

