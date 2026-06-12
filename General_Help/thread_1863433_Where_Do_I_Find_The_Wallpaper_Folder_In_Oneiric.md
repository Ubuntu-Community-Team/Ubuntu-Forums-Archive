---
title: "Where Do I Find The Wallpaper Folder In Oneiric?"
date: 2011-10-17
forum: General Help
---

### Post by stevedude on 2011-10-17
Does anyone know where to find the wallpaper folder in Ubuntu Oneiric 11.10?

I am not fond of how the wallpaper is changed in Oneiric from Natty. When I add a custom wallpaper via "Appearance" settings, it places it in the "Pictures Folder" drop-down menu choice where I have a gazillion pictures.

I would like to copy them to the default folder where Oneiric is grabbing the pictures from so I can select them from the "Wallpaper" choice.

Thanks in advance for any assistance.

---

### Post by collisionystm on 2011-10-17
/usr/share/wallpaper

I think

---

### Post by hwttdz on 2011-10-17
I think it's /usr/share/backgrounds.

That said I'd just make a ~/Pictures/wallpapers
and make a link from /usr/share/wallpapers to that folder, so then they'll appear as a subfolder in the wallpaper selection, and you won't have to enter the root password every time.

---

### Post by stevedude on 2011-10-17
You're are right hwttdz, it's usr/share/backgrounds. 

I thought it was /usr/share/wallpaper too at first like collisionystm stated, but I did not see the current backgrounds listed there so I knew that must have been from an earlier installation (Natty or Maverick).

I have the info I needed. Thanks to you both for quick replies!

---

