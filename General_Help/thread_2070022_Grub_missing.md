---
title: "Grub missing"
date: 2012-10-11
forum: General Help
---

### Post by mhacthoun on 2012-10-11
Dear brothers in Ubuntu,
   I ins
talled Ubuntu 12.04 (Unity) in my PC in which I also have XP Evo, but in re-starting I get a black screen with a warning of GNU Grub version..., saying:
  "Minimal BASH-like editing line supported". If I click Tab, it then gives me a bunch of command lines. I don't know what to do. Could anyone, please, help me out so I can get Grub selection page? Thanks, Tin

---

### Post by arandomstring on 2012-10-11
Well you are definitely going to need to give more info, but try running ```
ls
``` This will list the partitions on your hard drive. What you need to do next is find the one with Ubuntu installed by running ```
ls (hdX,Y)
``` Replacing X and Y with the numbers given in your options listed with the first command. You can tell which one is Ubuntu because it will be the only one that gives you output, listing a bunch of folders including boot/.

After you know which partition Ubuntu is on, run ```
set root=(hdX,Y)
``` to set this as the default location. Next run ```
set prefix=(hdX,Y)/boot/grub
``` (I'm not sure what this does, I'm just repeating what I heard elsewhere and know to work. Perhaps someone else can explain it?) Finally run ```
insmod /boot/grub/linux.mod 
```  and then ```
normal
``` to tell GRUB what module to load. This should bring you back to the GRUB selection screen. Hope it works, and I hope I was able to help! :p

---

### Post by mhacthoun on 2012-10-11
Tks for your reply, MadKristoff. Well, I have the Ubuntu installed in partition sda8 with the corresponding Swap in partition sda7. So, I'll take it from here in your explanation. If there's anything else you'll like to tell me, please, go ahead.

---

### Post by arandomstring on 2012-10-12
So you are going to need to replace X with 0 and Y with 8. (the 0 is the hard drive, the 8 is the partition)

---

