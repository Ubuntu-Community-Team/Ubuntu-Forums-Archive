---
title: "Grub 2 keeps resetting to defaults"
date: 2010-04-02
forum: General Help
---

### Post by Twizzle on 2010-04-02
I have installed 9.10 server edition on a headless PC and when installing told it to install security updates automatically.

As it is a server, I set up grub 2 to have a 2 second timeout then default to 0 and start.

The only problem is, every now and again I have rebooted the server to find I can't log back in. I then have to pull it all out from under the stairs and plug it into a monitor only to find that grub has reset to the default timeout option which does not have a countdown.

My etc/default/grub however has remained the same and if I update-grub, it is back to how I wanted it.

I think that the problem is arising when a new kernel is installed and grub somehow reverts and ignores what is in the /etc/default/grub file until I manually tell it to use it with update-grub.

Can anyone please tell me what I need to do to fix this as it is getting very tedious!

---

