---
title: "Bt4 RC1 &amp; Ubuntu 10.10,can't boot"
date: 2010-12-30
forum: General Help
---

### Post by heron7 on 2010-12-30
I added Bt4 RC1 to Ubuntu 10.10 , i noticed that  'Ubuntu is ext4 ',not that I'm complaining .
I allocated a 5'th of the disk space to Bt 4,now Ubuntu does'nt boot up . and root has moved to Bt 4.  Yes, i added a user . boot is still in Ubuntu .so i'm guessing it needs to be mounted? 
Recovery does'nt go either & i tried booting live cd & neither ..but i do get into HDD..
 I tried to editing  grub but my keys don't match,
 I can access it from Bt4  as root ,and from fedora 14 through partition editor on external drive.; 
this i found on Ubuntu's book on how to get back Ubuntu after installing windows

mount  /dev/sda1 /mnt
chroot  /mnt

then launch grub

grub>find /boot/grub/stage1
which gives the output  hd0,1

now to set root partition  :    grub> root (hd0,1)
 grub> setup (hd0,1)
 grub> exit 

i have tried recovery but i get 'error 15'
i've seen error 8, too ...

---

### Post by gordintoronto on 2010-12-30
Are you sure the instructions (from where?) are for the same version of grub you are using?

---

### Post by heron7 on 2011-01-03
[http://www.linux.com/archive/feature/113898](http://www.linux.com/archive/feature/113898) came across this ;)

---

### Post by heron7 on 2011-01-03
it gets better [http://www.linux.com/archive/feed/41263](http://www.linux.com/archive/feed/41263)  if the other option was a bit of finger full ..

---

### Post by heron7 on 2011-01-03
I Honestly ,honestly had'nt read that post completely ,but by god it reflects Exactly how i feel coming here or 'almost ' any other linux forum & It PAINS me , pfffff I don't get it do you want people or scientist & students again like way back when?... come on You Call It UBUNTU ...i am not a whiz but i,hell after a 6mnt i'm still a newbie .;but i love the whole idea though it has to be put as it is desired to be not as a competition with getting numbers ,even away from Windows...please Jono ,Marcel ,Matthew,Kristian....etc

---

### Post by gordintoronto on 2011-01-03
> **heron7 said:**
> it gets better [http://www.linux.com/archive/feed/41263](http://www.linux.com/archive/feed/41263)  if the other option was a bit of finger full ..

This is six years old! It's just not relevant today.

---

### Post by heron7 on 2011-01-07
but this is [http://www.brunolinux.com/05-Configuring_Your_System/Multiboot_grub.html](http://www.brunolinux.com/05-Configuring_Your_System/Multiboot_grub.html) , 'chainloading'.. 
I'm glad i found this site/forum.. really .. I read  up on Bruno.. :(  ,bon he sure lives on  :) Thanks Bruno

---

