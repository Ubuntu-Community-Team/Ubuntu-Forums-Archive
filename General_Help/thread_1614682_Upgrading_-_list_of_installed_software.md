---
title: "Upgrading - list of installed software"
date: 2010-11-05
forum: General Help
---

### Post by UBUminJ on 2010-11-05
Hello.
Finally, I found time to start moving from 8.10 to 10.10.
I now start preparing the moving (backup data etc).
I have installed quite a lot of software via the package manager, many of them I do not remember.
Is there a possibility to create a list of installed software in Ubuntu 8.10 ?
Thank you
MKE

---

### Post by Quackers on 2010-11-05
I think this may be what you're looking for

[http://linuxologist.com/1general/howto-fresh-ubuntu-install-without-losing-your-current-settings/](http://linuxologist.com/1general/howto-fresh-ubuntu-install-without-losing-your-current-settings/)

---

### Post by Tamlynmac on 2010-11-05
One quick thought:

In you Synaptic Package Manager on the lower left, if you select the "Status button", you can then select "Installed" from the left window.

Of course this won't show any firefox extensions, some addons or app settings.

system/adminstration/Synaptic Package Manager/status button/installed

Good Luck & hope this helps

---

### Post by deserthowler on 2010-11-06
dpkg -l > program.txt
Will give you a list of all of the programs installed.

Earl

---

### Post by garvinrick4 on 2010-11-06
```
sudo dpkg --get-selections>installedsoftware
```will put a file in your home folder with all packages alphabetically
The post above is rather nice with explanation of each package. Keep them both in home folder or documents handy to have around.

---

### Post by UBUminJ on 2010-11-06
Thank you guys, you gave me what I need.

---

