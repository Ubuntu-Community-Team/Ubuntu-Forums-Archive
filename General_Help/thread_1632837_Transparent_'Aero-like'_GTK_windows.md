---
title: "Transparent 'Aero-like' GTK windows ?"
date: 2010-11-28
forum: General Help
---

### Post by user1001 on 2010-11-28
Hi,

I was wondering if someone knows how to get the gtk windows to be transparent like on windows Vista/7,
compiz makes every element of the window transparent including the text, I do not want that.. only the window it self.

this has transparency but as you can see every element is transparent
[http://img69.imageshack.us/img69/7495/rgbagtk3.png](http://img69.imageshack.us/img69/7495/rgbagtk3.png)

Thanks..

---

### Post by akand074 on 2010-11-28
I think the only way to do that is to edit the actual theme. And I think you'd have to use other theme managers like Emerald-Themes not the default. I would just find a cool theme online that has transparency. [Heres]("http://browse.deviantart.com/?qh=&section=&global=1&q=Divergence#/d316eqx") one I've used that is kind of cool, though I really like the way it is by default to tell you the truth.

I don't know if you've thought about it before, but KDE I find is very windows-like in looks, it looks a lot like aero by default. I like Gnome better personally I don't want my system looking like windows but if you like the look you might want to consider giving it a try (or adding it to your current Ubuntu, you can choose to just boot into KDE instead of gnome at the login screen). You can check out the [Kubuntu]("http://www.kubuntu.org/") website.

---

### Post by user1001 on 2010-11-28
> **akand074 said:**
> I think the only way to do that is to edit the actual theme. And I think you'd have to use other theme managers like Emerald-Themes not the default. I would just find a cool theme online that has transparency. [Heres]("http://browse.deviantart.com/?qh=&section=&global=1&q=Divergence#/d316eqx") one I've used that is kind of cool, though I really like the way it is by default to tell you the truth.

I don't know if you've thought about it before, but KDE I find is very windows-like in looks, it looks a lot like aero by default. I like Gnome better personally I don't want my system looking like windows but if you like the look you might want to consider giving it a try (or adding it to your current Ubuntu, you can choose to just boot into KDE instead of gnome at the login screen). You can check out the [Kubuntu]("http://www.kubuntu.org/") website.

emerald is only for border... I don't want to edit a theme, the feature should be there ... 
I don't like kde either... and doesnt look like windows at all in my opinion.

---

### Post by WorMzy on 2010-11-28
That screenshot is of the Murrine engine, a GTK engine which has recently added support for transparency (apparently*)

I've tried to get it to work myself, but I've only managed to get my System Monitor to use the transparency effect, and I don't even know how I managed that tbh.

You can get the latest Murrine engine by adding this repository to your software sources: [https://launchpad.net/~elegant-gnome/+archive/ppa]("https://launchpad.net/~elegant-gnome/+archive/ppa"), and then installing the gtk2-engines-murrine package (sudo apt-get install gtk2-engines-murrine).

Once you have that package, you can configure your system to use it by using the gnome-color-chooser application. You can install that by running ```
sudo apt-get install gnome-color-chooser
``` (Though you'll need to enable the Universe repository before you can install that package)

Once you have gnome-color-chooser installed, you can open it from System -> Preferences -> GNOME Color Chooser. So open it up and click the "Engines" tab; tick the "Global" box, and set the engine to "Murrine". Then click Preferences (for global) and scroll down until you find the "Enable/Disable RGBA support" option. Check both boxes, then click OK, then Apply.

Maybe this image will be more explanatory:
[[IMG]http://img820.imageshack.us/img820/6751/picturefmf.th.jpg[/IMG]]("http://img820.imageshack.us/img820/6751/picturefmf.jpg")

---

