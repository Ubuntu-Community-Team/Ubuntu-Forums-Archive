---
title: "I get a &quot;no such partition&quot; error when tryint to boot into windows."
date: 2010-12-28
forum: General Help
---

### Post by amaruq_atka on 2010-12-28
When I try to boot into windows I get:

error: ba2c91dd44eda6e8
error: no such partition

I use Ubuntu 10.10, on an external drive setup to be first in boot order in the bios, windows internal drive second. It gives me a list every startup and I selected Windows XP this time. Unplugging the Ubuntu drive has no effect. I have never had such a problem before. It is Windows XP and it was installed with UNebootin. I have made no changes to any partitions. The Windows drive and data can still be accessed, just not booted into. How do I fix this?

---

### Post by Loyus on 2010-12-28
When you unplug your external drive, the grub loader still shows ?

---

### Post by amaruq_atka on 2010-12-29
It surprisingly does. Gives me two options for windows. One that says windows 2000 and one that says XP Professional. I have "solved" the issue myself I suppose. I have never done this before, but now I must load the windows 2000 option. It is strange. windows 2000 has never been installed on this machine. But its working and thats good.

---

### Post by coffeecat on 2010-12-29
It sounds as though you have two versions of grub floating around between your external drive and your internal one. So that we can get a better idea of what is going on, plug your external drive in, boot up Ubuntu and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the RESULTS.txt file. Please be sure to use [noparse]```

```[/noparse] tags as described in that link.

---

