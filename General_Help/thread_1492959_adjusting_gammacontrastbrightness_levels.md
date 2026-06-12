---
title: "adjusting gamma/contrast/brightness levels?"
date: 2010-05-25
forum: General Help
---

### Post by princeofnam on 2010-05-25
i'd like to better adjust my laptop screen's settings, but i have no idea how to set it to the correct sRGB settings, etc. as with windows.

---

### Post by Ozymandias_117 on 2010-05-25
If you have an nVidea or ATI gfx card, you can install their proprietary drivers and Control centers which will let you modify it.

---

### Post by princeofnam on 2010-05-25
is there no similar option with an integrated graphics card?

---

### Post by Ozymandias_117 on 2010-05-25
Your integrated may still be ATI or nVidia; if you aren't sure, you can use ```
sudo lspci | grep VGA
```

I'm sure there is a way to do it with intel cards, I just don't know what it is :P

---

### Post by princeofnam on 2010-05-25
it's neither ATI nor nVidia

i guess i should just continue bumping this thread.

---

### Post by cskeide on 2010-05-27
You can use the xgamma command to set gamma levels, for example:
```
xgamma -gamma 0.8
```

---

### Post by princeofnam on 2010-07-31
is there a way to adjust contrast levels though?

---

### Post by princeofnam on 2010-07-31
i also don't understand why xgamma only changes the gamma for one of my laptop screen and not my additional VGA monitor

---

