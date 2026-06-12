---
title: "&quot;Required icon theme not installed&quot; when theme activated"
date: 2012-01-12
forum: General Help
---

### Post by kkruecke on 2012-01-12
I added 
```
deb http://ppa.launchpad.net/webupd8team/themes/ubuntu natty main 
```
to my **/etc/apt/sources.list.d/** because I wanted to try the **clearlook-revamp-gtk-theme**. But when I go to System Settings->Appearance and activate "clearlook revamped", there is a message in the dialog box stating:

>  the icon theme 'elementary monochrome' is missing. 

I don't know what package 'elementary-monochrome' is part of, or why it wasn't automatically installed as a dependency?

---

### Post by Frogs Hair on 2012-01-12
Under Gnome 2 custom  themes often have/ had a recommended icon set so they appear as advertised. This will not affect your ability to use the theme and for me such messages simply disappeared over time . You can download Elementary icons at the link if you choose . [http://danrabbit.deviantart.com/art/elementary-Icons-65437279](http://danrabbit.deviantart.com/art/elementary-Icons-65437279)

---

### Post by kkruecke on 2012-01-12
Thanks for the reply and the link to download it. Into what directory should it be unpacked?

---

### Post by raja.genupula on 2012-01-12
just drag it into appearance window

---

### Post by kkruecke on 2012-01-12
I extracted the icons from [http://danrabbit.deviantart.com/art/elementary-Icons-65437279](http://danrabbit.deviantart.com/art/elementary-Icons-65437279) into **/usr/share/icons**, but I still get the same message when I tried to activate clearlooks-revamp:

> The theme will not look as intended because the require icon theme 'elementary-monochrome' is not installed.

---

### Post by raja.genupula on 2012-01-12
ok open your appearance window and click at customize . There are you seeing that named icon theme which you extracted ?

---

### Post by kkruecke on 2012-01-12
Now that I extracted it, I do see (under the Icon tab of Customize), "elementary", "elementary Dark", and "elementary-monochrome". But its folder icon, unlike "elementary" or "elementarty Dark" has a question mark in it. I don't know what that indicates?

When I choose the Clearlook Revamp" theme, "elementary-monochrome" is automatically selected for the Icons --I see this when I choose Customize->Icons, but its not being recognised for some reason.

---

### Post by kkruecke on 2012-01-13
> You can download Elementary icons at the link if you choose . [http://danrabbit.deviantart.com/art/...Icons-65437279](http://danrabbit.deviantart.com/art/...Icons-65437279)

Evidently, **elementary-monochrome** icons are not part of elementary icons.

---

