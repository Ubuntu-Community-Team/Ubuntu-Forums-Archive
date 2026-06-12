---
title: "Compiz Wobbly windows question"
date: 2009-09-12
forum: General Help
---

### Post by Kamrua on 2009-09-12
I was wondering if I can make it that when moving the windows around, they don't blur slightly. It's not that bad, but I'd like it more, if it was more pixelish.

---

### Post by mac9416 on 2009-09-12
Hey, Kamrua,

You can tweak the heck out of Compiz with compizconfig-settings-manager. Whether or not you can edit the blur factor for the wobbly windows, I'm not sure, but it's worth a look.

To install, go to System>Administration>Software Sources and enable the Universe and Multiverse repositories. Then install compizconfig-settings-manager:
```
sudo apt-get install compizconfig-settings-manager
```

Good luck
-mac

---

### Post by Kamrua on 2009-09-12
Thanks mate, but I already have this. I was wondering if I were to edit the settings to something, it would stop blurring... But I guess not :(
Thanks, though!!

---

### Post by mcduck on 2009-09-12
> **Kamrua said:**
> I was wondering if I can make it that when moving the windows around, they don't blur slightly. It's not that bad, but I'd like it more, if it was more pixelish.

Disable antialiasing from your graphics card's settings if you have such option. Or try setting the Texture Filter-setting to something else under General options in Compiz.

Blurring is not a feature of the Wobbly Windows-plugin. It's something that happens because your graphics card tries to antialias the graphics, or because it's not able to draw the moving windows with high enough quality and framerate to keep them sharp.

---

### Post by marcmy on 2010-06-02
just wanted to say changing texture filter to fast fixed this for me. thanks a bunch :)

---

