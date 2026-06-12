---
title: "need help modifying my grub"
date: 2010-05-12
forum: General Help
---

### Post by MasterShihoChief on 2010-05-12
After the fail of installing 10.04 on my fakeraid, i successfully installed 9.10. It installed grub 0.97 and grub was able to boot to ubuntu just fine. Only one small hiccup is grub does not see my windows 7 partition on this fakeraid. 

I'm pretty sure i know what happened. I used to run truecrypt on the windows side before i wanted to dual boot. So the windows bootloader is on a small 300mb partition outside windows. I assume this is why grub didnt recognize it. I can still mount the windows patition and everything is fine, windows didnt die XD. I can also mount and have access to the boot partition with all the boot stuff in it. Only problem is I have no idea how to reconfigure grub to make it chainload or whatever it has to do to get it to work, I'm kinda newb with bootloaders and ubuntu XD.

Thanks for any help

---

