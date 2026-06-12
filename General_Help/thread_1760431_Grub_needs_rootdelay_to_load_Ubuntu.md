---
title: "Grub needs rootdelay to load Ubuntu"
date: 2011-05-16
forum: General Help
---

### Post by chris.dangerfield on 2011-05-16
I have installed Ubuntu on my custom-built PC and one of the issues that I have is that the Grub configuration needs "rootdelay=1500" (1500 or some similar number) added to the menu entry that loads linux. 

Some have suggested that this is an issue with the Linux kernel, but there have been several updates since I loaded Ubuntu onto the computer and it is still an issue - particularly as every upgrade needs me to go and correct the default grub configuration. Does anyone have any ideas of what this problem might be due to?

Thanks heaps,

Chris

---

### Post by tc0nn on 2011-07-13
On all of our newer dell's we have to add rootdelay=90 or else it bails out to the initramfs prompt.

---

