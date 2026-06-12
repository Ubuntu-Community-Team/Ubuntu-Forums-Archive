---
title: "LibreOffice broke my OpenOffice install"
date: 2011-02-25
forum: General Help
---

### Post by Scooter_X on 2011-02-25
So yea, I wanted to try LibreOffice out. I found a PPA for it, so I added the source, tried it out, didn't like it, and noticed that openoffice now won't work. Which isn't too big of a deal, but now I can't even get the software center to install it. It gives me some error that you can read in the screenshot. What can I do?

---

### Post by TuxIsAwesome on 2011-02-25
Libreoffice from what I have heard is replacing OpenOffice.org in 11.04.

[LEFT]The two are not compatible, eg one has to be completely uninstalled before the other will install.

Libreoffice is also supposedly free of Oracles evil grip, and is going to be, or better developed than OpenOffice.org.

The error you are getting is normal, I get the same error when I attempt to install Openoffice.org when Libreoffice is installed.

Just use Libreoffice, it's the same thing but better.

[/LEFT]

---

### Post by kiyop on 2011-02-26
Could you install openoffice.org, after completely remove(uninstall) libreoffice by synaptic?

System -> Administration -> Synaptic

---

### Post by ubuntu27 on 2011-02-26
After completely removing/uninstalling libreoffice, 
remove the PPA as well.

Update the repository (Reload in Synaptic)
And then install OpenOffice.org

---

### Post by Scooter_X on 2011-02-26
I did uninstall (using synaptic) all of libreoffice's stuff.

I didn't actually REMOVE the ppa, but I did unselect it. Would that have made the difference?

---

### Post by Hagar Delest on 2011-02-27
OOo and LibO can perfectly run together on the same system, see the screenshot below.

But to do so, better avoid the PPA repositories. Install them from the .deb provided on their site. For the installation, follow that tutorial: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

