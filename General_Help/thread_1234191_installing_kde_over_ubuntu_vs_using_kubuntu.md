---
title: "installing kde over ubuntu vs using kubuntu"
date: 2009-08-07
forum: General Help
---

### Post by diggedy on 2009-08-07
Is there any difference in performance installing the kde desktop on top on ubuntu against using a dedicated kde distro such as kubuntu?

---

### Post by wojox on 2009-08-07
Open a terminal:
```
sudo apt-get install kubuntu-desktop
```
Reboot the computer, and when you get to the login prompt, click the Options button in the lower left hand corner pick KDE Session. It will load KDE instead of Gnome. If you want Gnome back just log out and do the option for Gnome.

---

### Post by diggedy on 2009-08-07
thanks but I think you misunderstand the question. Ive tried doing this but I was wondering if having the two side by side would cause any detrimental effects to system performance. I know when plasma has crashed it has shown my gnome desktop wallpaper making me think gnome or at least some processes are running in the background

---

### Post by aysiu on 2009-08-07
There will be no adverse effect on system performance, but you may notice a few annoyances that pop up:

1. After you log out of KDE and back into Gnome, there will be a .desktop file that shows up on the desktop (this .desktop file is actually meaningful in KDE but just shows up as a useless file in Gnome).

2. Your applications menu in both KDE and Gnome will be cluttered with redundant applications from the other desktop environment.

3. Your boot usplash theme may be wrong for your desired desktop environment (it may be Ubuntu for Kubuntu or Kubuntu for Ubuntu).

---

### Post by diggedy on 2009-08-07
These redundant applications, are they useable in both environments? and can I uninstall them if not needed?

---

### Post by bodhi.zazen on 2009-08-07
> **diggedy said:**
> These redundant applications, are they useable in both environments? and can I uninstall them if not needed?

Yes, you can use KDE applications in gnome and gnome apps in KDE.

Removing redundant applications is a bit trickier.

I suggest you try kubuntu and if you like it install kubuntu-desktop.

If the redundant applications bother you, back up your data and do a fresh install (yes you can remove gnome or KDE, but it can also be more hassle then it is worth considering a fresh install takes so little time).

---

### Post by nikhilbhardwaj on 2009-08-07
don't get me wrong
but kubuntu isn't the best implementation of kde
try opensuse or mandriva instead if you want to see how good kde can be.

ubuntu is awesome for gnome and xubuntu for xfce

---

### Post by diggedy on 2009-08-07
> **nikhilbhardwaj said:**
> don't get me wrong
but kubuntu isn't the best implementation of kde
try opensuse or mandriva instead if you want to see how good kde can be.

ubuntu is awesome for gnome and xubuntu for xfce

Im currently running opensuse kde at the minute but im finding more support for the likes of ubuntu and also ubuntu seems to be more up to date in terms of the kernel. Ive tried kubuntu but it was a nightmare, maybe karmic might be better but at present its not working too well for me.
Mandriva on the other hand seemed awesome but for some reason the desktop effects didnt seem to work well and after a few reboots it suddently stopped loading, this happened on two seperate installs.

So im now deciding to try kde installed on ubuntu or mint (64 bit versions)

---

