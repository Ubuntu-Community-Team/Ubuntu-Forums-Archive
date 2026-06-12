---
title: "Ubuntu Software Center closes after &quot;install&quot; is clicked"
date: 2010-07-04
forum: General Help
---

### Post by ShadowWraith on 2010-07-04
I have kubuntu since I like KDE, but I loathe Kubuntu's package manager gui. To solve that, I installed gtk and the Ubuntu Software Center.

Every time I hit install for any package in the software center and give my password, the window closes. The installation completes, but I cannot navigate to any page listing the package that is being installed except the "installation in progress" page without the window closing.

Help please?

---

### Post by warfacegod on 2010-07-04
I'm not sure how to do this in KDE but I've helped a number of people with U.S.C. by showing them how to change it's command to gksudo software-center instead of /usr/bin/software-center. Since you are in KDE, I don't know if the sudo should be gksudo or kdsudo (think it's kd anyway). In Gnome it would be a matter of right clicking the Menu bar and selecting Edit Menus> finding the Ubuntu SC and clicking Properties. Again, I don't know KDE well enough to know if that's the way it's done.

---

### Post by ShadowWraith on 2010-07-04
Well, I accessed the menu editor through right-clicking the KDE button, and changed the command for the Software Center to kdsudo, which caused it to drop instantly. Looks like kdsudo is the problem, and that the Software Center isn't compatible with it.

I then changed it to gksudo, which I also have installed, and now it works.

Thanks for the info!

---

### Post by warfacegod on 2010-07-04
Glad to help. I wasn't entirely convinced it *would* work, either way.


Another satisfied customer of warface Industries: Divinity Division.:P

---

### Post by Blue Rose on 2010-07-12
I just wanted to mention that for kde it is 'kdesudo' not kdsudo :-) Using either gksudo or kdesudo will work, though I still think this is a bug in software center. 
Users should be able to browse around as normal user and only give admin power when they really want to install something. I hope this will be fixed soon. :-)

---

