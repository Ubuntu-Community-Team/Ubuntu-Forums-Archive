---
title: "Desktop Manager does not start anymore and Grub does not show a menu"
date: 2011-10-15
forum: General Help
---

### Post by vatikan on 2011-10-15
Hello everybody,

I upgraded my system to 11.10. So that worked fine so far. However, after having installed gnome-session-fallback I got a somehow messed up gnome desktop with missing icons etc. Well that doesnt really matter as I decided to switch to KDE. I installed KDE the usual way and it worked fine. Then, when I wanted to shut down I somehow managed to lock KDE. The whole screen was behind that "unsharp" mask and I couldnt do anything anymore. I then shut down on the shell. 
So the next time I started up the desktop manager wouldnt come up anymore. I get plymouth and it simply stops at one point. I only see the 4 dots. I checked for plymouth trouble shooting under [http://wiki.ubuntuusers.de/plymouth](http://wiki.ubuntuusers.de/plymouth) and found that I should try to disable plymouth using kernel parameter. However, since the install of 11.10 I don't have any GRUB menu anymore. It simply boots without seeing grub...
So the question is how the hell do I get back into the grub menu? I saw that I have to change the grub menu.lst, but thats not possible as I cannot boot into the system. I can't switch into a console when plymouth hangs, so there is no way to change anything. 

As I am using WUBI (please don't be mad ;) ) booting the system using a boot cd is not so easy. So any other solution (press a key at one point or similar) would be appreciated.

thanks

---

