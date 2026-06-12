---
title: "why does ubuntu show sans-serif fonts as serif"
date: 2010-06-26
forum: General Help
---

### Post by thered on 2010-06-26
I do a little bit of web design, used to use Windoze until I found Quantas.

What I have noticed is the Ubuntu plus Firefox seems to display sans-serif fonts as serif.

If you check this site in Ubuntu and Windows in FF or Chrome or IE they show different fonts

[http://redcartown.net]("http://redcartown.net") or this one, which I didn't write,

[http://www.fansonline.net/middlesbrough/mb/index.php]("http://www.fansonline.net/middlesbrough/mb/index.php")

You will see the displayed fonts are different.

I have the full fonts package installed - ttf-mscorefonts-installer

Can anyone explain this, don't want to go back to windows for web design but it's a PITA having to boot to windows to check it.

---

### Post by thered on 2010-06-27
Anyone?

---

### Post by Spr0k3t on 2010-06-27
I checked both pages and found the fonts are rendered close to the same.  So a took out a VM of a clean install of XP and Ubuntu10.04.  The clean install did show the fonts as serif fonts.  The problem was the settings inside Firefox.  Change the default font (Edit -> Preferences -> Content -> Default font).

Don't forget to update the font cache just in case.

```
fc-cache -f
```

---

### Post by thered on 2010-06-28
thanks spr0k3t :)

I've edited the settings. 

I also need to check my CSS too I think. - Blagging a free template so not all my own code :)

---

