---
title: "Use grub instead of grub2?"
date: 2010-07-05
forum: General Help
---

### Post by Meskarune on 2010-07-05
I like grub better than grub2. Would it be possible for me to use grub instead? Are the complications from "downgrading" ? For the life of me I cannot get grub2 to boot any operating systems installed in a logical disc partition. (I have 4 OS's installed on my computer, one windows 7, the rest linux flavors)

---

### Post by kellemes on 2010-07-05
Hi there..
Does this work?
[https://help.ubuntu.com/community/Grub2#Uninstalling GRUB 2]("https://help.ubuntu.com/community/Grub2#Uninstalling GRUB 2")

When installing *buntu using the alternate installcd you can choose you're bootloader, including grub-legacy and lilo.. afair.

---

### Post by oldfred on 2010-07-05
I have several versions of Ubuntu installed in logical partitions and have not had any issues with grub2. Grub2's osprober is a lot better at finding other systems.

With old grub you either chainloaded to keep it simple or had to totallly come up with a correct boot entry. You can still chainload if you have old grub in the partition of your other linux installs.

---

