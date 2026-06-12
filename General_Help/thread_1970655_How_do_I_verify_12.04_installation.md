---
title: "How do I verify 12.04 installation"
date: 2012-05-01
forum: General Help
---

### Post by niranjan_rao on 2012-05-01
My system is standard system and gave me no trouble so far. In other words I have standard packages from trusted sources and no fancy customization of any packages or otherwise. I am happy with unity and like the way things are. This is my primary work machine.

Something bad happened during update to 12.04 from 11.10. I got BSOD and was not even able to boot.

After the crash I did reboot in recovery mode and chose the menu option (forgot exactly what it was, but dpkg something) and it allowed me to login in gnome mode. Had some fun with unfamiliar desktop, could not figure out how to logout or may be it was half baked installation and hence other buttons were not showing up.

After that I ran update manager which told me about half done update. When asked to proceed it told me can not upgrade from 12.04 to 11.10 (with release names).

Had much better luck with apt-get. It showed me bunch of packages left aside which I installed manually. At one point "details wideget" under settings was showing 12.04 however I had older kernel 3.0.*. Not sure how that happened.

After spending 4-5 hours of time my machine seems to be usable except one nagging thing. Something is prompting me to enter my password every few minutes - I get a dialog box about authentication is required ot change user data and details box shows org.freedesktop.accounts.user-administration. This tells me everything my not be right.

I have lost confidence about integrity/stabilitty of the machine. How do I verify my installation is proper. That dialog box may be result of bad configuration, but not sure what needs to be changed.

---

### Post by niranjan_rao on 2012-05-01
shameless bump

---

### Post by jerrrys on 2012-05-01
Open a terminal and

sudo apt-get dist-upgrade

see if that fixes anything

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by Frogs Hair on 2012-05-01
```
lsb_release -a 
``` Will display release ```
uname -a
```Will display kernel version .

---

