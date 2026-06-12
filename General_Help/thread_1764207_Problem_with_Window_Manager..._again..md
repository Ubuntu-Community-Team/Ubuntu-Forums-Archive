---
title: "Problem with Window Manager... again."
date: 2011-05-21
forum: General Help
---

### Post by galacticaboy on 2011-05-21
Ok yesterday I had a problem where I tried to install some Emerald themes on Xubuntu 11.04. It did not work and in the process, all of my Windows Decoration was gone, the Maximize and Minimize buttons at the top of each windows were gone, as shown in the picture attached. I am done with emerald, I uninstalled, I just want my top windows bars back. I found a command for the terminal that fixed it, but when I turned my PC on this morning, the bars were gone again, and I had to reenter that command again. The command it 'xfwm4 --display=:0.0 --replace' that brings them back. Is there a way for my computer to automatically do that command or is there another permanent solution?

---

### Post by galacticaboy on 2011-05-21
***bump***

---

### Post by Toz on 2011-05-21
There are two ways that I can think of:

1. Close all the applications on your desktop and click on the "Log Out" option from the main menu. Check the "Save session for future logins" checkbox and logout. Log back in and you should be good.

2. Add it to the Autostart applications (Settings Manager->Session and Startup->Application Autostart tab.

---

### Post by friv_livs on 2011-05-21
remove all the 'xubuntu' packages, and install 'xfce4' package.

do leave gnome-icons-theme though, as it is lighter than what synaptic replaces it with (KDE icons).

---

### Post by galacticaboy on 2011-05-22
> **friv_livs said:**
> remove all the 'xubuntu' packages, and install 'xfce4' package.

do leave gnome-icons-theme though, as it is lighter than what synaptic replaces it with (KDE icons).

If I do this my system will not break will it? I have had way to many systems break on me by doing this sort of thing, and I cannot handle that anymore. I am tired of re downloading all of my files and stuff.

---

### Post by galacticaboy on 2011-05-22
> **Toz said:**
> There are two ways that I can think of:

1. Close all the applications on your desktop and click on the "Log Out" option from the main menu. Check the "Save session for future logins" checkbox and logout. Log back in and you should be good.

2. Add it to the Autostart applications (Settings Manager->Session and Startup->Application Autostart tab.

Actually this worked! Thanks! And I already have all of the XFCE4 packages installed.,

---

