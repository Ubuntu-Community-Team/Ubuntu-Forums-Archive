---
title: "Grub2 rescue"
date: 2010-07-29
forum: General Help
---

### Post by Rey117 on 2010-07-29
I have resized my Ubuntu 10.04 partition to install WIndows (i need it for school) and reboot and it came up with the grub rescue screen. 

To make a long story short i found out that the Set root =(hd0,8) and set prefix=(hd0,8)/boot/grub/ is set wrong and should be set to hd0,6. i did this through grub rescue however i need to stay on hd0,6 when i reboot. 

How do I go about doing this?

---

