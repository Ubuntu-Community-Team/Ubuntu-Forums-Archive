---
title: "problem with booting hp probook 4515sh"
date: 2010-07-27
forum: General Help
---

### Post by bui89 on 2010-07-27
hello i have hp probook 4515s with ati card, which prevents normal boot of ubuntu: i get blank blacki screen. When i had dual boot with windows i could edit grub for succesfully booting. Now I can't view grub. Are there any key to press for getting to grub? Please help me :)

---

### Post by dino99 on 2010-07-27
at end of bios process, hold "shift" key down to view grub menu

but you should see it by default because of dual booting:


sudo apt-get update
sudo apt-get install -f

sudo grub-mkconfig
sudo update-grub

---

### Post by bui89 on 2010-07-27
I had dual boot now I deleted windows partition and reinstalled ubuntu on all hard disk, so I dont see grub. 
shift helps than you very much
:(

---

