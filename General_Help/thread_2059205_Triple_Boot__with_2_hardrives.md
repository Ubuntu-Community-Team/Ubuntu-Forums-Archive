---
title: "Triple Boot  with 2 hardrives"
date: 2012-09-17
forum: General Help
---

### Post by rilians on 2012-09-17
I just purchased a new computer that has windows 7 on the hardrive. I am swapping it out and putting in my other hardrive which has Ubuntu 10.04 and 12.04 on it. Both drives SATA. I am using Grub Customizer. I am going to keep the Windows HD as a second drive. I have read that there are no master/slave for sata drives. My Ubuntu drive is on the first channel. So I would like to triple boot. Will Customizer pick up the Windows Drive? I originally had ubuntu drive set up on the 2nd channel, but customizer did not add it. I can see the windows drive in Ubuntu. I guess I can go behind the scenes and set it up. But rather not if I can help it. Would appreciate some help either way. Love Linux....started right up with new computer. I am not new to linux.
 
Thanks
Claude

---

### Post by ajgreeny on 2012-09-17
I've never used grub-customizer, preferring to do things the "manual" way by editing the various config files as that means I get to understand grub a lot better.
However, the first thing you will need to do is boot to ubuntu (you may have to play around in the BIOS with the boot device priority to get that to happen) andf then run sudo update-grub to add in the windows 7.

You should then be able to boot to either OS when the ubuntu disk has boot priority, but if the other disk is first boot device you will go straight to windows 7.

---

