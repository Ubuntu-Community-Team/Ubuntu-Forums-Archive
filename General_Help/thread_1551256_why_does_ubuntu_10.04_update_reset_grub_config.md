---
title: "why does ubuntu 10.04 update reset grub config?"
date: 2010-08-12
forum: General Help
---

### Post by suzenon on 2010-08-12
In 9.10 after kernel update there was always prompt window if i want to do changes in grub config file. In 10.04 there's no such question and every time i do update i have to edit my grub config file in order to get rid of older kernels and set windows as second position in boot menu.

Any clue why does it happen and how to stop updates overwrite my grub config?

---

### Post by Admiral Yi on 2010-08-12
When I update I get a question asking if I want to keep the old config files. Though when I updated yesterday, it did add new kernels to the list.

I guess you could always copy the scripts in /etc/grub.d and then put them back there when you're done updating. You'd still have to manually remove old kernels though.

---

### Post by suzenon on 2010-08-12
Weird, it doesn't ask me a single question... i think something is broken then.

What these scripts do?

---

### Post by Admiral Yi on 2010-08-12
With grub 2, it loads the scripts in that folder to add the options to the boot menu. It means you don't edit the config files directly, which is apparently easier. I think if you just copied them and then put them back afterwards it would keep your grub the same. You would have to run update-grub as well.

---

