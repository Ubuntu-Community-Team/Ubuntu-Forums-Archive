---
title: "How can I make the black toolbar on top transparent Ubuntu 11.10, I included the pic"
date: 2011-11-13
forum: General Help
---

### Post by Lukasz Tarkowski on 2011-11-13
How can I make the black toolbar on top transparent Ubuntu 11.10, I included the pic, and also change the text color for font, on that toolbar

---

### Post by quequotion on 2011-11-13
> **Lukasz Tarkowski said:**
> How can I make the black toolbar on top transparent Ubuntu 11.10, I included the pic, and also change the text color for font, on that toolbar

There is a setting in ccsm for transparency.

```
apt-get install compizconfig-settings-manager
```

In the settings for Unity, under the "Experimental" tab there is "Panel Opacity"

As for the font color, it depends on your theme.

In gtk3 there's no GUI to change the colors individually.

I use the default theme with an invisible panel and an invisible cube with a dark skydome (an equirectangular picture of the river seine at the moment) and this looks very nice.

Unfortunately there doesn't seem to be any way to actually hide the panel. Invisible or not, it owns that part of the screen. Notice in this screenshot, even when the cube is mid-rotation the panel is still across the top of the screen. Some things can appear under it, like fullscreen video or games, but nothing will appear over it.

---

