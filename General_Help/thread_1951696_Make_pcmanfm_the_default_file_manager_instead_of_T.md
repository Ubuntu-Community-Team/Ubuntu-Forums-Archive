---
title: "Make pcmanfm the default file manager instead of Thunar"
date: 2012-04-02
forum: General Help
---

### Post by sfang on 2012-04-02
As the title says, I want to make pcmanfm the default file manager instead of Thunar. I used Synaptic to install pcmanfm and set it as the desired  manager in "Preferred applications". However, when I open a new window, be it through Places or desktop, look for a file with Smplayer, Firefox or LibreOffice, I still get Thunar. Actually, the only way to get pcmanfm to show up is through the terminal.
  
 So how can I make pcmanfm the default file manager for all operations? I searched around, but didn't find a good answer and the help [page]("https://help.ubuntu.com/community/DefaultFileManager") isn't exactly helpful... 

I'm on Xubuntu 12.04 beta 2.

---

### Post by techvish81 on 2012-04-02
I think you will have to remove thunar,  because the preferred application settings does not work as needed,  so if you remove it, pcmanfm will be the only available filemanager . but there could be weird consequences,  still you can try and see what happens.( keep record of what you removed to return to previous working state)

---

### Post by brainwash on 2012-04-03
Does the command
```
exo-open --launch FileManager
```
open pcmanfm or thunar?


The desktop is managed by xfdesktop, which opens folders with thunar (default). If you are talking about the places plugin for xfpanel, it relies on thunar to mount removable devices and needs to be patched to correctly use the preferred file manager.

So removing thunar would be the easiest solution, but maybe not the best.

There is also also a site with detailed instructions:

[http://stuff.body-builders.org/xfce-replace-thunar-with-pcmanfm/](http://stuff.body-builders.org/xfce-replace-thunar-with-pcmanfm/)

---

### Post by sfang on 2012-04-03
> **brainwash said:**
> Does the command
```
exo-open --launch FileManager
```open pcmanfm or thunar?


It opens pcmanfm.

I think removing Thunar might not be the best course of action, but I'll see how it goes. I'll try the steps listed in brainwash's link too and report my findings later. 

Thanks for the help.

---

