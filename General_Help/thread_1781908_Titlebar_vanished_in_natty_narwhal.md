---
title: "Titlebar vanished in natty narwhal"
date: 2011-06-14
forum: General Help
---

### Post by aisajib on 2011-06-14
I was disabling Desktop Wall and enabling Desktop Cube in CompizConfig settings manager (advanced) in my newly installed Natty Narwhal (Classic desktop) then suddenly the title bars from the windows vanished. The title bar is the top bar of every window that contains the title as well as minimize, maximize and close buttons. I've restarted the machine still the bars aren't there. Can anybody help me with this situation? It's urgent, actually.

---

### Post by jake.anq on 2011-06-14
Hi

As a temporary measure, I would suggest un-installing Compiz.  This should switch back to gnome-wm automatically (well, it did on my system).
```
sudo apt-get remove compiz compiz-core compix-gnome
```
After that, if you want to try again, install the package 'compiz'
```
sudo apt-get install compiz
```
This will re-instate all of the necessary dependencies.
Note:  If you do this (and you use Unity), **Unity will dissapear.**  You will be back with the old style desktop until you re-install Compiz.

---

### Post by smithark on 2011-06-14
go to compiz settings manager--> window decoration and enable it. This solved the issue for me. 
Otherwise, you could try the below tutorial (though i havent tried this myself):
[http://ubuntugenius.wordpress.com/2011/05/22/ubuntu-11-04-fix-enable-emerald-themes-for-compiz-fusion-window-borders-title-bars/](http://ubuntugenius.wordpress.com/2011/05/22/ubuntu-11-04-fix-enable-emerald-themes-for-compiz-fusion-window-borders-title-bars/)

anyway, good luck!

---

### Post by aisajib on 2011-06-14
> **smithark said:**
> go to compiz settings manager--> window decoration and enable it. This solved the issue for me. 
Otherwise, you could try the below tutorial (though i havent tried this myself):
[http://ubuntugenius.wordpress.com/2011/05/22/ubuntu-11-04-fix-enable-emerald-themes-for-compiz-fusion-window-borders-title-bars/](http://ubuntugenius.wordpress.com/2011/05/22/ubuntu-11-04-fix-enable-emerald-themes-for-compiz-fusion-window-borders-title-bars/)

anyway, good luck!

Thanks, dear. Enabling Window Decoration did the trick for me. Thanks again for saving me. :)

---

### Post by leonbravo on 2011-06-21
yes, It does the trick. 

Every time I minimised a window, the 3 window's buttons disappeared, I was feeling already scare of clicking in the minimise button. just feeling nuts ...

Thanks..

---

### Post by justhamade on 2011-07-04
Need to install it first via 
```
sudo apt-get install compizconfig-settings-manager
```
Then you can go to System Settings->CompizConfig Settings Manager and search for Window Decoration uncheck it, then recheck it and done.

---

### Post by wildmanne39 on 2011-07-05
> **aisajib said:**
> I was disabling Desktop Wall and enabling Desktop Cube in CompizConfig settings manager (advanced) in my newly installed Natty Narwhal (Classic desktop) then suddenly the title bars from the windows vanished. The title bar is the top bar of every window that contains the title as well as minimize, maximize and close buttons. I've restarted the machine still the bars aren't there. Can anybody help me with this situation? It's urgent, actually.
Hi, if you still want the cube and effects in natty here is a guide to get it working.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

### Post by JD8182 on 2011-09-03
I fixed this issue by simply opening system/preferences/CompizConfig settings manager: Preferences/Profile Backend tab/reset to default (under profile) / reboot. hope this might help.

---

