---
title: "Docky and screen usage"
date: 2011-01-23
forum: General Help
---

### Post by Robbyx on 2011-01-23
I tried out docky and found that it restricted the screen size so that even if it was hidden I lost about 2" off the bottom of the screen. It was a black area.

I expected to be able to hide docky and use the full screen. 

**Could I have done anything to prevent the blanking of the base of the screen?**

---

### Post by edhplus2 on 2011-01-23
In case no one else responds: I know it has something to do with installing compiz, which you can find in the software center. Someone else should know more about it, but that might get you started.

---

### Post by psusi on 2011-01-23
compiz is the default window manager; you don't need to install it.

I set my docky to intelihide and maximized windows use the full screen just fine.

---

### Post by Halzen on 2011-01-23
Regardless of your Compiz installation (which, yes, is available by default on recent distros), you need to ensure that you have compositing available and activated. This may involve downloading and installing proprietary graphics drivers, as was the case for my GTX 260.

---

### Post by Robbyx on 2011-01-23
I am unclear as to the direction of the answers because I use dual screens and until I installed docky, applications used the full space on both the screens. 

With docky it was as if it was reserving a few inches at the bottom of the screen just for itself. Without docky the panels disappear below the edge of the monitor and the full screen is available. With docky, docky disappears but there is a band of black which is no longer used by the other applications.

Robin

---

### Post by kerry_s on 2011-01-23
> **Robbyx said:**
> I am unclear as to the direction of the answers because I use dual screens and until I installed docky, applications used the full space on both the screens. 

With docky it was as if it was reserving a few inches at the bottom of the screen just for itself. Without docky the panels disappear below the edge of the monitor and the full screen is available. With docky, docky disappears but there is a band of black which is no longer used by the other applications.

Robin

like others have said, docky requires composting, so you would need normal effects enabled. else you can use xcompmgr or metacity compiz, but it's not as fast nor configurable as compiz.

just in case you don't know, right click the desktop-> change desktop background, then click the last tab.

---

### Post by Robbyx on 2011-01-24
Thank you. I have it working properly. How do I adjust the compiz settings? Some of the effects I do not like.

---

### Post by kerry_s on 2011-01-24
> **Robbyx said:**
> Thank you. I have it working properly. How do I adjust the compiz settings? Some of the effects I do not like.

if it's a docky effect you do it in docky setting(front anchor icon), for compiz you need to install "compizconfig-settings-manager".

docky doesn't have much settings as far as docks go.

docky = just plain old dock
avant-window-navigator = a dock with more features
cairo-dock = dock with more features then you could need

i use the awn ppa version.

---

### Post by Robbyx on 2011-01-24
Thanks for that advice. I have just installed avant and am using it.

Robin

---

### Post by Robbyx on 2011-01-28
I use aMSN. I tried adding it to AWN but the icon was not correct it was generic. I put into the awn task manager /usr/share/amsn/amsn.


I have a similar problem with PcMan not showing the correct icon in the gnome panel.

[B]How can I ensure that the original icon for the app is shown in a panel or in awn?
[/B]

---

### Post by kerry_s on 2011-01-28
> **Robbyx said:**
> I use aMSN. I tried adding it to AWN but the icon was not correct it was generic. I put into the awn task manager /usr/share/amsn/amsn.


I have a similar problem with PcMan not showing the correct icon in the gnome panel.

[B]How can I ensure that the original icon for the app is shown in a panel or in awn?
[/B]

drag & drop the icon you want for it to the app on awn, you'll get a pop up.

---

### Post by Robbyx on 2011-01-29
> **kerry_s said:**
> drag & drop the icon you want for it to the app on awn, you'll get a pop up.

Your thumbnail showed an icon changer. Where do I find it?

---

