---
title: "Icon Set Creation"
date: 2009-07-20
forum: General Help
---

### Post by tom.swartz07 on 2009-07-20
Hey everyone-

I have a really basic question. Recently Ive been dabbling at gnome-look getting various icon themes. There is one theme in particular that I like, but there are some icons that I would like to customize myself. for example, the 'Refresh' icon is broken for some reason, (i would like to change it), the 'close tab' icons dont seem to fit either. 

My question is; Is there a simple way to create your own icon themes? I have found a program called Gnome Icon Builder, but it doesnt seem to work for what I am trying to do. 

Is there an easy way to import icon sets, and edit them easily, even through the file browser or command line?


ANY help would be appreciated! Until I could figure this out, Im stuck with the 'broken image' icon for the reload icon throughout gnome.

---

### Post by CatKiller on 2009-07-20
> **tom.swartz07 said:**
>  Is there an easy way to import icon sets, and edit them easily, even through the file browser or command line?

Icon themes that you've downloaded and applied will be stored as a single directory in either ~/.icons or /usr/share/icons. As long as your image file is in the right place and is called the right thing, it will be used. The right name and right place are outlined [here]("http://www.freedesktop.org/wiki/Specifications/icon-theme-spec"). As a practical first step, though, you might find it most useful to find a theme whose icon does work and compare that to the theme you wish to use. Rename the broken image accordingly, or make a symbolic link that has the correct name.

---

### Post by tom.swartz07 on 2009-07-20
Hey Thanks! 

Those were the exact locations that I needed to look. I found the file that was incorrect and fixed it!

Thanks again!

---

