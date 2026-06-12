---
title: "DVD Drive Problems"
date: 2010-03-16
forum: General Help
---

### Post by thevor on 2010-03-16
Hey,

I have been trying to install a game and am having a lot of problems. The game I am trying to install is World of Warcraft, and the method I have chosen to attempt is using Wine, and PlayOnLinux(POL). Everything went smoothly with the downloads and installations of wine and POL, but I always get to problems during installations.

Basically, I get to the point in the installation where I have to tell the POL installer where the Installer.exe file is, and when I point to it, it says:


wine: could not load L"D:\\Installer.exe": Module not found


I have gone into the wine configuration, and made sure that the D: is pointed at my dvd drive. In doing this, I found then when I put the dvd in, I could navigate it at two different points:

/media/cdrom

and

/media/cdrom0

Using either file manager, or terminal, I could navigate my way to the same files on the dvd at each of these locations. What I am wondering is if it is normal to have two separate mount points for one dvd, and if this could somehow be what is preventing POL from locating the Installer.exe file when I try to point it in the right direction.

Any help would be greatly appreciated. Thanks in advance.

Trev

---

