---
title: "Uninstalling Mac4lin :("
date: 2009-08-27
forum: General Help
---

### Post by yam.matt on 2009-08-27
Hello all,
         Recently I installed Mac4lin theme pack for Ubuntu 9.04 version, but after installing I didn't like it so tried to uninstall it using the uninstall script that came with it, but it didn't do anything! So I tried to change it using the default theme manager in Ubuntu, it changed many things to normal but somethings remained unchanged, for example the maximize, minimize and exit buttons were still situated to the left, and the icon of the show desktop button in the bottom panel also remained the mac4lins one.
          I need a simple solution to change the complete theme back to the way it was when I installed Ubuntu.
            I shall be very thankful to anyone who helps:).

---

### Post by Liolikas on 2009-08-27
Try to create now user account.

---

### Post by yam.matt on 2009-08-27
But I want to change the theme in my current acoount.

---

### Post by Liolikas on 2009-08-27
Probably you messed too much there is no other choice, but bring everything back one after other then. Still create other user and use his .* files as reference. You can try simply:
cp ~oteruser/.* ~/.*
BUT DANGEROUS you can create even more mess!!!

---

### Post by NoaHall on 2009-08-27
Are you using Emerald theme manager? If so, open it, Edit Themes -> titlebar -> title-bar object layout: 
and change it to "HM:T:N(2)R(2)C"

---

### Post by yam.matt on 2009-08-27
Sorry but I am not using Emeral theme manager, just the default one.

---

### Post by infra_red_dude on 2009-08-28
Just goto Systems > Preferences > Appearances and select either Clearlooks or Human theme.

I'm wondering how come the uninstall script didn't work for you. It works for me.

---

### Post by toniliu on 2009-09-23
> **yam.matt said:**
> Hello all,
         Recently I installed Mac4lin theme pack for Ubuntu 9.04 version, but after installing I didn't like it so tried to uninstall it using the uninstall script that came with it, but it didn't do anything! So I tried to change it using the default theme manager in Ubuntu, it changed many things to normal but somethings remained unchanged, for example the maximize, minimize and exit buttons were still situated to the left, and the icon of the show desktop button in the bottom panel also remained the mac4lins one.
          I need a simple solution to change the complete theme back to the way it was when I installed Ubuntu.
            I shall be very thankful to anyone who helps:).


Hey,,i HAve same Problem too,,i'm using 8.10 intrepid. Have You try this one in terminal?

                                 gconftool-2 --set /apps/metacity/general/button_layout --type string "menu:minimize,maximize,close"

---

