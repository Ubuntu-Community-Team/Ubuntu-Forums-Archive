---
title: "Can't log on my machine"
date: 2011-12-17
forum: General Help
---

### Post by Salahuddin on 2011-12-17
I was running ubuntu then i have installed windows 7 which has eaten the boot file of ubuntu and it was log on windows directly 
  then i have tried to reinstall grub on ubuntu using live cd using the following commands 



```


  *    sudo mount /dev/DEVICENAME_FROM_STEP_ONE /mnt*
[I]  sudo rm -rf /boot 
  sudo ln -s /mnt/boot /boot
  sudo grub-install --root-directory=/mnt/ /dev/sda
  [/I]*sudo update-grub*
*
```*

  then restart my labtop
  but when restarting nothing appear but a black screen with some words finished by 
  grub>
  now i can't log on any OSes except using live cd
  what i have to do ...help me please ..

---

