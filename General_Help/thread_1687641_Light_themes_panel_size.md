---
title: "Light themes panel size"
date: 2011-02-14
forum: General Help
---

### Post by whalogreg on 2011-02-14
When using the 'light themes' on a fresh install, the panel will not let me re-size below 26px . This forces the theme's default panel background image to repeat itself at the bottom of the panel.(shown in one of the attached images)

When using a cutom image (set to 26px height) or a background color instead of an image, the original theme's background image is still forced behind certain parts of the panel, i.e. indicators/menus.. (also shown in one of the attached images)

All other themes allow me to re-size below 26px. Where could I start troubleshooting this problem?

---

### Post by whalogreg on 2011-02-17
::bump::

---

### Post by whalogreg on 2011-02-19
::bump::

---

### Post by Krytarik on 2011-02-19
I have the Lucid versions of the "Light Themes", so it is a bit different. My "Ambiance" version is set up to a default panel height of 24px, the panel background image is exactly that high. It seems as if the new version has a higher image included, following the package listing you should find it here:
"/usr/share/themes/Ambiance/gtk-2.0/apps/img/panel.png"

If it is indeed 30px high, scale it down to your desired height, but you may also not get lower than 24px, it is somehow blocked by the panel menu.

---

### Post by whalogreg on 2011-02-19
> **Krytarik said:**
> I have the Lucid versions of the "Light Themes", so it is a bit different. My "Ambiance" version is set up to a default panel height of 24px, the panel background image is exactly that high. It seems as if the new version has a higher image included, following the package listing you should find it here:
"/usr/share/themes/Ambiance/gtk-2.0/apps/img/panel.png"

If it is indeed 30px high, scale it down to your desired height, but you may also not get lower than 24px, it is somehow blocked by the panel menu.

On my laptop (Maverick) the default panel size is 24 px, which confuses me because on my desktop (Maverick as well) the default is 26 px (and will not let me set it under 26 px), but the panel image is 24 px which causes the problem..

---

### Post by Krytarik on 2011-02-19
> **whalogreg said:**
> On my laptop (Maverick) the default panel size is 24 px, which confuses me because on my desktop (Maverick as well) the default is 26 px (and will not let me set it under 26 px), but the panel image is 24 px which causes the problem..
Sorry, I got distracted by another included panel backround that is 30px high.

That is indeed weird, are both updated?

I will download the theme package from the "maverick-updates" repo and check the "gtkrc" file, it is in the "gtk-2.0" dir.

---

### Post by Krytarik on 2011-02-19
Sorry, I had first to install the current version of the murrine engine through its PPA. The new themes indeed are very light, but not bad.:)

So, when I chose the new theme, it fitted perfectly my panel, which is 24px, without changing anything. When I make the panel higher than 24px, I get the same look like in your screenshot. FYI, when you choose a different background via the properties dialog, those background will always only fill the middle part of the panel, not the menus, indicators and buttons (taskbar).

---

