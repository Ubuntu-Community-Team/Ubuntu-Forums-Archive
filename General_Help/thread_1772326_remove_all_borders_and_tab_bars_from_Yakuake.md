---
title: "remove all borders and tab bars from Yakuake?"
date: 2011-05-31
forum: General Help
---

### Post by 13east on 2011-05-31
machine: kubuntu 11.04x64 w/ kde4

    the top terminal is of Yakuake w/ "No Border" option already enabled
    the bottom is of Konsole w/ "No Border" option also enabled

how do I remove all borders from Yakuake to make it resemble Konsole at the bottom so as only the transparent terminal portion is visible?

if not possible what is a better replacement to Yakuake that has true no border settings, as well allows drag/drop of texts into the terminal? Already tried Tilda but it doesn't allow you to drag and drop texts into the terminal; tried Guake but can't get it to work in Kubuntu.

---

### Post by Zorael on 2011-05-31
You could try editing the theme, I guess. I don't think you can get rid of the tab bar in any other way than to set the entire bar to 0 pixels, save modifying the source.

A feature request for the KDE bugtracker, perhaps? :3

See [this existing bug](https://bugs.kde.org/show_bug.cgi?id=222538), too.

---

### Post by 13east on 2011-05-31
> **Zorael said:**
> You could try editing the theme, I guess. I don't think you can get rid of the tab bar in any other way than to set the entire bar to 0 pixels, save modifying the source...

How do i edit Yakuake's theme to bring the tab bar to 0 pixels?

---

### Post by Zorael on 2011-06-07
I randomly found this theme; [One Pixel Title](http://kde-look.org/content/show.php/One+Pixel+Title?content=142441).

---

### Post by 13east on 2011-06-07
> **Zorael said:**
> I randomly found this theme; [One Pixel Title](http://kde-look.org/content/show.php/One+Pixel+Title?content=142441).

I found the same theme today through Akregator's default "KDE Look" feed.
I've attached a screenshot; very clean look but for the one-pixel line at the button edge.

Thank You.

---

### Post by lariosa42 on 2011-08-27
I like this modification, but I still wanted the tab bar (which for me is already set to partially transparent).  I just wanted to get rid of the title, which apparently cannot be made transparent (without a recompile or something).  To do this, download One Pixel Title, as suggested by others, and then did

```

sudo cp -r onepixeltitle /usr/share/kde4/apps/yakuake/skins/onepixeltitle_mod 
sudo cp -r /usr/share/kde4/apps/yakuake/skins/default/tabs /usr/share/kde4/apps/yakuake/skins/onepixeltitle_mod  
sudo cp -r /usr/share/kde4/apps/yakuake/skins/default/tabs.skin /usr/share/kde4/apps/yakuake/skins/onepixeltitle_mod  

```

Then select "onepixeltitle_mod" in the settings, or edit the "Skin" setting under "[Apperence]" in this file:
```
sudo gedit ~/.kde/share/config/yakuakerc
```
to say 
```
Skin=onepixeltitle_mod
```

---

