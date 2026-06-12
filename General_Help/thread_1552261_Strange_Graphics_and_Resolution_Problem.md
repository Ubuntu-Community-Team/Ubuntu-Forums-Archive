---
title: "Strange Graphics and Resolution Problem"
date: 2010-08-13
forum: General Help
---

### Post by madmax.santana on 2010-08-13
I own an HP HDX-16 notebook PC and I recently installed Ubuntu Lucid on it. Ever since I have upgraded my system, there has been a strange resolution problem bothering me.
Before update (after fresh install) the splash and the tty have been coming in a good resolution. The resolution of my desktop is 16:9 1366x768, and the resolution of the splash was exactly the same. I know so because the Ubuntu logo appeared natural.
Now, after the upgrade, the desktop resolution is fine, the same. But the resolution of the splash is reduced to 800x600. It is easy to notice since the logo appears larger than life and stretched. The visage is pathetic (Windows 95 :P). Similarly, the resolution of tty 1-6 has decreased to a lower resolution. I never expected the tty to be widescreen, but a higher resolution looks better even with the x-elongated font. As of the current situation, font appears very large, which looks very odd. And the elongation of fonts is more obvious.
All I want is to make the graphics of splash and tty like before.
Any help will be appreciated.

---

### Post by themusicalduck on 2010-08-13
Do you have an Nvidia or ATI card? Since Lucid uses Plymouth for the splash screen, the closed drivers don't handle the graphics properly.

There is a workaround which I used from here -  [http://www.ubunturoot.com/2010/04/how-to-get-plymouth-working-with.html](http://www.ubunturoot.com/2010/04/how-to-get-plymouth-working-with.html) but it isn't guaranteed to work (it did for me, but I heard it messed up the boot for someone else).

As for the TTY resolution, perhaps install Startup-Manager (I think it's in Software Centre) and set the resolution on there under Display. I think this should set the TTY resolution.

---

### Post by madmax.santana on 2010-08-14
Thanks man!
It didn't work though. Ultimately I did as explained here.

[URL="https://help.ubuntu.com/community/ChangeTTYResolution"]https://help.ubuntu.com/community/ChangeTTYResolution
[/URL]
EDIT:
This is more helpful, and even better
[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

---

