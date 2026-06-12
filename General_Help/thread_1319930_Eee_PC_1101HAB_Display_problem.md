---
title: "Eee PC 1101HAB Display problem"
date: 2009-11-08
forum: General Help
---

### Post by xgriffonx on 2009-11-08
I'm running 9.10 on an Asus Eee PC 1101 HAB. Periodically, the screen will glitch (normally just becoming a jumble) and the only way fix is to reboot the system. I looked at the display settings and it's showing an unknown display, but I'm not sure where to find drivers for this model. Has anyone else run into this problem or know a fix? Thanks.

---

### Post by luptinpitman on 2009-11-28
Just installed 9.10 UNR on a new EeePc 1101HAB and am seeing the video corruption you describe.

[http://vip.asus.com/forum/view.aspx?board_id=20&model=Eee+PC+1101HA&id=20091109065144968&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=20&model=Eee+PC+1101HA&id=20091109065144968&page=1&SLanguage=en-us)

---

### Post by luptinpitman on 2009-11-28
Actually this fixed it completely:  [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

wget [http://gma500re.altervista.org/scripts/poulsbo_ppa.sh](http://gma500re.altervista.org/scripts/poulsbo_ppa.sh) && sh ./poulsbo_ppa.sh

---

### Post by fred_rider on 2009-11-29
My system was experiencing the video problem described here. The suggested fix worked.
Thank you.

---

### Post by fred_rider on 2009-11-29
Problem re-manifested itself... previously the display went wacko when I tried to run Firefox. Now Firefox works fine. The problem now emerges when I try to run any update of the Ubuntu system. I want to install Ruby on Rails but cannot do so.... the screen keeps going wacko.

---

