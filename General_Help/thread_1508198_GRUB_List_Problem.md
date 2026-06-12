---
title: "GRUB List Problem"
date: 2010-06-12
forum: General Help
---

### Post by davethepilot on 2010-06-12
Hello all. I'm new to Ubuntu and Linux in general. Just using it out of curiosity. I'm interested in editing the Grub startup menu to take out some of the previous versions of Ubuntu. First, is there a reason Grub keeps the previous versions available to boot to in that list? If it is just in case of a problem with the new installation wouldn't it make sense to only have the most recent previous installation?

Anyway here is the problem, when I run:
```

"gedit /boot/grub/menu.lst" 

```
The editing program opens the file named "menu.lst" but the file is empty. How is it possible for this file to be empty yet I have multiple boot options and they all work? Does anybody know what I am running into here? I appreciate any help!

Thanks and have a great day!
David

---

### Post by oldfred on 2010-06-12
If you have the newer versions of Ubuntu then you have grub2. Grub2 uses a grub.cfg file that you do not edit but update with settings from one file and scripts or text from another.

You can delete older kernels but generally recommend to keep 2 so you can boot an older one if every needed. Besure not to delete the one you are using or you will not be able to reboot.

In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

You can also not show the kernels in the grub menu.
See section on editing script to only show 2 entries:
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

More info
General info:
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by davethepilot on 2010-07-05
It's been a crazy month. Got myself moved out to California and finally got back to looking at this again a couple days ago. The Synaptic Package Manager instructions linked from a different post were perfect. Thanks so much for your help!!

---

