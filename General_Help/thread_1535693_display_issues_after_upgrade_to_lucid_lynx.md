---
title: "display issues after upgrade to lucid lynx"
date: 2010-07-21
forum: General Help
---

### Post by ap_nat on 2010-07-21
After upgrade to lucid lynx I was unable to login (it used to loop), reinstalled gdm, removed nvidia* packages, now though I am able to login, but the default screen is set to 338x211 with this message in Xorg.0.log "II) intel(0): Setting screen physical size to 338 x 211", I can start gnome-session from this terminal which opens up normally. I am out of ideas to get the default screen size to normal. (xorg.conf never had anything special [no dirver names])

---

### Post by bigfatgooglefat on 2010-07-22
Make sure you reinstall the nvidia drivers. Without those, you're running on fallback drivers which run at that low res.

---

### Post by ap_nat on 2010-07-23
I have a intel 945 VGA card, so I do not need the nvidia drivers, I got them in the process of upgrade, I can use icewm and do not get the screen size issues, I get the problems only while using metacity. A fresh reinstall of metacity solved the problem.

---

