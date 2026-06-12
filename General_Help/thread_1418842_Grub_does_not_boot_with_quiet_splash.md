---
title: "Grub does not boot with quiet splash"
date: 2010-03-01
forum: General Help
---

### Post by Skumleren on 2010-03-01
Being a complete newcommer to linux, please excuse any lack of information in this post.

I have just installed ubuntu on top of my windows 7 installation, on its own partition. From the beginning i could not install from the cd since it just froze every time i pressed install from the installation window. I got the commandline for the command to show itself, and noticed a command called quiet splash in the end. Wanting to see if it was hiding any errormessages i deleted it and ran the installer again. Now the installer did not crash and instead installed with no complications.

Ok i thought, wierd, but no real problem. I was wrong of cause.

In grub, when i try to boot windows 7 there is no problem. When i try to boot ubuntu it crashes. Ive left my computer for 30 minutes and still nothing has happened.
However when i press e to see the boot command, delete quiet splash and press ctrl-x for boot, ubuntu starts with no problems.

I have no idea what soever as to why this isnt working, but can it be a hardware issue?
If noone can figure out what the problem is, is there a way to change the command line in grub so i dont have to delete quiet splash every time i boot?

---

### Post by plucky on 2010-03-01
> **Skumleren said:**
> Being a complete newcommer to linux, please excuse any lack of information in this post.

I have just installed ubuntu on top of my windows 7 installation, on its own partition. From the beginning i could not install from the cd since it just froze every time i pressed install from the installation window. I got the commandline for the command to show itself, and noticed a command called quiet splash in the end. Wanting to see if it was hiding any errormessages i deleted it and ran the installer again. Now the installer did not crash and instead installed with no complications.

Ok i thought, wierd, but no real problem. I was wrong of cause.

In grub, when i try to boot windows 7 there is no problem. When i try to boot ubuntu it crashes. Ive left my computer for 30 minutes and still nothing has happened.
However when i press e to see the boot command, delete quiet splash and press ctrl-x for boot, ubuntu starts with no problems.

I have no idea what soever as to why this isnt working, but can it be a hardware issue?
If noone can figure out what the problem is, is there a way to change the command line in grub so i dont have to delete quiet splash every time i boot?

See [here](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2)

You have to edit **/etc/default/grub** and remove **quiet splash** and then **sudo update-grub** to update grub boot. 

Good Luck

---

### Post by Skumleren on 2010-03-01
Thank you that worked flawlessly. I'm still puzzled as to why quiet splash crashed in the first place, but now its running as intended at least.

---

