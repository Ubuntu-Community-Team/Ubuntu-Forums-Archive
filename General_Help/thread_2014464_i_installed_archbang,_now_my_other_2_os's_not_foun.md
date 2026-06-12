---
title: "i installed archbang, now my other 2 os's not found in grub? please help"
date: 2012-07-02
forum: General Help
---

### Post by slixz85 on 2012-07-02
hi. i just installed archbang and my wifi works on it thankfully, I am BRAND NEW to pacman if anyone can help me. I need to get back to ubuntu to stay. this showed me i don't know squat.
normally sudo update-grub is what i have always used in ubuntu/debian but i am confused what to type in archbang. i aint goin to those forums cuz this is just a grub bootloader problem. i have ran into this before but can't remember what i did or how i worked around it. my other two os's were solus and bodhi. thanks to any help.

i was just planning on using archbang for gaming since it is so light on memory but now i will just stick with bodhi or wattos.

thanks

---

### Post by Redblade20XX on 2012-07-02
What bootloader does archbang have? If it's anything like arch linux, you probably got the default grub. Ubuntu and other distros use grub2 so grub will not detect those oses.

You'll either need to upgrade your bootloader to grub2 in archbang.
See here: [https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)

Or get a Ubuntu live cd and use boot repair to recreate grub2 bootloader.

-Red

---

