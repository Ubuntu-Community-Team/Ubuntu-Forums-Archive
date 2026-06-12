---
title: "Dreaded Reinstall"
date: 2010-09-01
forum: General Help
---

### Post by chapacha on 2010-09-01
So basically I just need some help with juggling some partitions. I need to reinstall Windows again so I wondering what is the best way to go around doing that? I already backed up my personal files I want to keep on the Windows partition so I don't need any backing up tools. My plan is to wipe the Windows partition and reinstall it. So my question is, what is the best way to do this? Oh and also I DO NOT want to wipe my Ubuntu partition, that is where I backed up my Windows files I wish to keep.

Thanks!
chapacha

P.S. Any information on conflicts with Grub and stuff like that when I wipe it would be much appreciated.

---

### Post by rbc on 2010-09-01
If you are using grub2, see here:
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

If you are still using grub legacy, look here:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Scroll down to the section entitled Installing Windows after Ubuntu

---

### Post by 73ckn797 on 2010-09-01
You can boot from the Ubuntu CD and use System/Administration/GParted to resize, move and format your partitions. The grub issues are already referenced in prior reply.

---

