---
title: "Cant get past grub"
date: 2010-10-29
forum: General Help
---

### Post by elejele on 2010-10-29
Hey guys i'm having an issue with booting

I installed ubuntu via wubi and dual boot windows. After ubutntu became unresponsive for 10+ minutes, being the impatient person that i am, i did hard reboot. dumb idea i guess

When I select ubuntu from the boot menu it goes straight to the gurb boot loader

I the method described here:

[http://ubuntuforums.org/showpost.php?p=8396043&postcount=5](http://ubuntuforums.org/showpost.php?p=8396043&postcount=5)

which has worked before, but to no avail. instead when I try to load the kernel i get the following message :

unknown file system

does anyone I can get past this?

by the way, I'm very new to linux

---

### Post by bcbc on 2010-10-29
You will want to run fsck on the root.disk - it sounds like it's been corrupted. Use the method described in the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?")

Try to avoid hard shutdowns on wubi, use ALT+SysRq R-S-U-B instead.

---

### Post by elejele on 2010-10-29
Thank you, that did the trick. For the record no mounting was necessary just the following

```
sudo fsck path/root.disk 
```

---

### Post by bcbc on 2010-10-29
> **elejele said:**
> Thank you, that did the trick. For the record no mounting was necessary just the following

```
sudo fsck path/root.disk 
```

Great - glad it worked :)

Yes, you're right. In fact, you should never run fsck on a mounted file system. The wubi guide should probably be updated to clarify this.

---

