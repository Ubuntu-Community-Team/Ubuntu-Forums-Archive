---
title: "reconfiguring grub"
date: 2006-02-01
forum: General Help
---

### Post by korkow on 2006-02-01
hey, i just instlled windows XP 64 bit (my dad bought a copy for himself, so i decided to install it over windows 2k). I use windows soley for some programming and games. Anyways, i was stupid and forgot its bad to install windows after linux. Anyways, how do I make it so I can boot back to linux again (which is my primary OS).

I already have a kubuntu (breezy) live CD, and the windows are in C:\WINDOWS (win xp64) and C:\WINNT (win 2k)

---

### Post by devipl on 2006-02-02
Make starting boot disk for your windoze
boot from Livecd, then
open shell ececute sudo grub 
then execute
grub> root (hd0,0) (- that means /dev/hda)
grub> setup (hd0)
grug> quit

sudo reboot (after  reboot you shoul see grub....

after taht you should add windoze to grub
sudo vi /boot/grub/menu.lst
############
#search for #hiddenmenu (delete # that will make appear #all systems before boot
title windoze
rootnoverify (hd0,1) #which means dev/hda1 *check #where is yor windoze
makeactive
chainloader +1
#########you are almost done!
#then sudo grub-install /dev/hda

#regards

---

