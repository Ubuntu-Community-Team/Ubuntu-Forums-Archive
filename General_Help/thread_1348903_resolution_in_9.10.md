---
title: "resolution in 9.10"
date: 2009-12-07
forum: General Help
---

### Post by Dave Otter on 2009-12-07
How can I get screen resolution of 1280 +760 in 9.10
    Thanks

---

### Post by tcturner on 2009-12-07
hey whats up dave merry christmas
i've had problems with screen refresh and resolution rates. did a lot of xorg.conf editing. some cards act well others welllll. best way i found is generate a modeline and add it to xorg.conf under monitor. go to a terminal and type gtf 1280 760 and it will generate a modeline. if you want a refresh rate add it to the end (gtf 1280 760 85) where 85 is the refresh rate in hz if you want 85?. in the terminal type gksu nautilus enter your password and you will be in root nautilus go to places computer filesystem etc X11 and open xorg.conf go to file save as xorg.conf_backup and save. open xorg.conf_backup now add the modeline from terminal ( when you did the gtf command above it'll still be there copy and paste it) to monitor section in xorg.conf_backup and save as xorg.conf log out and back in should have entry under screen in preferences menu
good to search ubuntu community docs too a lot of info there
hope it helps

---

### Post by tcturner on 2009-12-07
> **tcturner said:**
> hey whats up dave merry christmas
i've had problems with screen refresh and resolution rates. did a lot of xorg.conf editing. some cards act well others welllll. best way i found is generate a modeline and add it to xorg.conf under monitor. go to a terminal and type gtf 1280 760 and it will generate a modeline. if you want a refresh rate add it to the end (gtf 1280 760 85) where 85 is the refresh rate in hz if you want 85?. in the terminal type gksu nautilus enter your password and you will be in root nautilus go to places computer filesystem etc X11 and open xorg.conf go to file save as xorg.conf_backup and save. open xorg.conf_backup now add the modeline from terminal ( when you did the gtf command above it'll still be there copy and paste it) to monitor section in xorg.conf_backup and save as xorg.conf log out and back in should have entry under screen in preferences menu
good to search ubuntu community docs too a lot of info there
hope it helps

great link [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

