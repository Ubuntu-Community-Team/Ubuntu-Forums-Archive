---
title: "Window flashes &amp; disappear on clicking 'Computer' icon"
date: 2009-10-17
forum: General Help
---

### Post by nbkonline on 2009-10-17
When I click the 'computer' icon on my ubuntu 9.04, The window opens for a second and then disappears ! I'm in trouble. Thank God that I can access the mounted partitions through other options. The problem is that due to this I'm not able to browse my mobile device through bluetooth, as whenever I click on 'computer' or 'browse device' the window flashes off... Plz plz help to solve this problem...  I've installed ubuntu tweak and made a shortcut of 'my computer' on the desktop, when double clicked the same thing happens... I'm really frustrated of this..

---

### Post by stinkeye on 2009-10-17
> **nbkonline said:**
> When I click the 'computer' icon on my ubuntu 9.04, The window opens for a second and then disappears ! I'm in trouble. Thank God that I can access the mounted partitions through other options. The problem is that due to this I'm not able to browse my mobile device through bluetooth, as whenever I click on 'computer' or 'browse device' the window flashes off... Plz plz help to solve this problem...  I've installed ubuntu tweak and made a shortcut of 'my computer' on the desktop, when double clicked the same thing happens... I'm really frustrated of this..
Did you you use ubuntu tweak to set show desktop and which icons to show.
I'm on jaunty and there was a problem with the show desktop command in U/tweak and is no longer available in the current release,
(Ubuntu Tweak 0.4.9.1) although you can still select which icons to show.
Could try unticking and then reticking show desktop from the configuration editor 
```
gconf-editor
```
and goto /apps/nautilus/preferences/show_desktop
You can set which icons to show in /apps/nautilus/desktop

---

### Post by hxm on 2009-10-25
Hallo,
I also have the same problem which started after i used ubuntu tweak...Using the gconf-editor didn't fix the problem

Any other idea???

---

