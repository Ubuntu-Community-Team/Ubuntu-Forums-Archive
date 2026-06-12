---
title: "selling laptop, whats the easiest way to delete everything?"
date: 2010-09-01
forum: General Help
---

### Post by Scarecrow3517 on 2010-09-01
Hey i'm selling my laptop and I want to wipe it first. It's duel booting ubuntu and vista but vista is infected and not booting. Whats the easiest way to get rid of everything on it? preferably i would want to leave ubuntu and remove vista and all installed programs and files. I don't mind wiping everything off it though.

thanks

---

### Post by Bachstelze on 2010-09-01
Probably better to wipe everything, you never know who could get their hands on it. Just use good ol' dd:

```
sudo dd if=/dev/urandom of=/dev/sda
```

From a Live CD of course, no filesystem on the drive must be mounted.

---

### Post by mike555 on 2010-09-01
Boot into ubuntu live cd , start gparted , then format the partitions you want to erase , but don't delete them or it will mess up grub .......... then boot up and "update-grub" 

--- of course if you want to erase it all then format it all (from the live cd)......

---

### Post by Scarecrow3517 on 2010-09-01
thanks for the help but i don't think i have a livecd, i downloaded ubuntu. 

what else can i do?

---

### Post by AlphaLexman on 2010-09-01
Do you want to sell the laptop with an OS on it, or without?

---

### Post by Marlonsm on 2010-09-01
You can always use a pendrive as liveCD.
Take a look here for a how-to (there is plenty of them in the internet):
[http://www.howtoforge.com/easy-way-to-create-bootable-ubuntu-usb-pendrive](http://www.howtoforge.com/easy-way-to-create-bootable-ubuntu-usb-pendrive)

---

