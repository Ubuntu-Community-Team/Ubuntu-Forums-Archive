---
title: "gnome Panel Problems"
date: 2010-12-02
forum: General Help
---

### Post by jlangholzj on 2010-12-02
So, Posted here before on this issue and no help whatsoever. Lets try again, I've got a little more info this time as well.
 
Gnome panel is being really weird. The top panel has "disapeard" completely. When I maximize a window however, there is a blank spot where the panel should be. 
 
I've tried every single line of terminal prompts that i could find on the internet and none of them work. So PLEASE do not say "this will restore your gnome panel so do this" becuase it has no effect.
 
also, I've tried to uninstall/install gnome and after un-installation i can fully maximize windows without the gap. However upon installation of gnome panel again it just disapears again and is back to its previous state. 
 
Also, on boot, i can select between 2.6.35-23 and 2.6.32-25 and if i choose the older of the two it will pop up only its partially "hidden". But then i can click on it, move its location to left/right and then back to the top and its normal. Thats just annoying.
 
this has happened with both 10.04 and 10.10 for me. 
 
I'm currently at work but once I get back I'll try and take some screenshots.
 
any ideas? am I just going to have to uninstall and re-install ubuntu completely orrrr?

---

### Post by philinux on 2010-12-02
This will reset the panels back to there default settings.

Open a terminal.

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by jlangholzj on 2010-12-02
did nothing, brought my btm panel back (that i deleted becuase i use docky) but still the gaping hole on top.

here's some screen shots i got of what it looks like:

[IMG]http://i260.photobucket.com/albums/ii35/jlangholzj/screen1.jpg[/IMG]



also this error popped up when i ran the above script

[IMG]http://i260.photobucket.com/albums/ii35/jlangholzj/Screenshot.png[/IMG]

could my theme have anything to do with it? I guess thats about the only thing I've not tried.

---

### Post by jlangholzj on 2010-12-04
bupidy

---

