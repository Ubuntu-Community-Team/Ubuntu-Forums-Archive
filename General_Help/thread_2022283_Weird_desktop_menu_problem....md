---
title: "Weird desktop menu problem..."
date: 2012-07-10
forum: General Help
---

### Post by Lateralus138 on 2012-07-10
Hello all, I started with Ubuntu as the main Linux distro for my dual boot with Windows and had added Kubuntu-desktop and Lightdm just to check them out and for a while everything was ok, but I hadn't been back to my regular Ubuntu desktop for quite some time and the other day I went to check it out and there wasn't a Launcher or panel at the top. I tried dist-upgrading and checking all my other desktops and noticed there were these Openbox options (that I think came from the Kubuntu?) I then check all the other entries that said Openbox in them and none of them seemed to work correctly. After checking every other desktop I came last to Ubuntu 2D; which, I figured was the least important place to check and lo and behold it was a perfect running regular Ubuntu desktop, fully functional with my Docky and compositing working and everything. Even my Devil's Pie settinsg work. Anybody have any clue on how I should go about correcting some of these menu options and desktops? I like my regular KDE Plasma desktop, it runs and looks smooth. It just seems only the the things that are OPenbox, 3 or 4 desktop versions and Ubuntu are the only things that don't run correctly and the entry for the regular Ubuntu by itself, Lightdm and KDE Plasma and Ubuntu 2d which works like regular Ubuntu all run great. Is there a way to remove open box stuff and leave everything safe with maybe only a few small fixes and set the Ubuntu 2D entry as just Ubuntu?

Edit: Well I went back to my regular Gnome desktop and now it's panel is now missing. I liked it because it was black, it wasn't the regualar gnome-panel, does anyone know the name of the black panel so I can run it? I went back to Ubuntu 2D and looked at the task manager and realized it was running unity-2d-shell and so I killall unity-2d-shell and started unity and it runs fine, but back on the regular Ubuntu desktop when I run regular unity it wont start.

---

### Post by Lateralus138 on 2012-07-10
Ok, I solved this myself, I caused all these problems myself messing around with compiz, My Unity and Ubuntu Tweak settings and  installing xcompmgr for lxde, but I had the .desktop autostart set to run for all of my desktops and so I removed the desktop entries except for lxde and xfce and the Gnome and Unity versions of Ubuntu are working fine now. The only thing that doesn't work are the Openbox entries, I'm still not exactly sure what that comes from.

---

