---
title: "Basic Themes Info?"
date: 2012-08-30
forum: General Help
---

### Post by Adam's AI on 2012-08-30
I have never applied custom themes to my linux box, but am very interested in doing so. For someone just approaching it, it seems a bit daunting, because there are so many **kinds** of themes. I currently run Lubuntu 12.04, and as far as I can tell, I can use GTK2 themes, emerald themes and OpenBox themes, but have also seen resources suggesting I can use GTK3 themes. But can I also install themes for qt apps separately?

So really:
Where can someone who has never explored themes in linux go to find basic information on how to use the different kinds of themes out there?

Thanks.

---

### Post by Frogs Hair on 2012-08-30
For Ubuntu 12.04 with the default Unity desktop you need Gnome 3.4 compatible themes and you can locate many at the link. [http://gnome-look.org/index.php?xcontentmode=167](http://gnome-look.org/index.php?xcontentmode=167)

Search the forum or internet for installation instructions for 12.04 because the question of has been addressed many times.

---

### Post by Adam's AI on 2012-08-30
> **Frogs Hair said:**
> For Ubuntu 12.04 with the default Unity desktop you need Gnome 3.4 compatible themes and you can locate many at the link. [http://gnome-look.org/index.php?xcontentmode=167](http://gnome-look.org/index.php?xcontentmode=167)

Search the forum or internet for installation instructions for 12.04 because the question of has been addressed many times.

Thank you for the quick reply! I'm actually running Lubuntu as I mentioned, but I was wondering if there were general Linux theme-related info people could link me to, as it seems like multiple kinds of themes (beyond simply gnome 3.4) that will work on a given setup.

---

### Post by vasa1 on 2012-08-30
> **Adam's AI said:**
> I have never applied custom themes to my linux box, but am very interested in doing so. For someone just approaching it, it seems a bit daunting, because there are so many **kinds** of themes. I currently run Lubuntu 12.04, and as far as I can tell, I can use GTK2 themes, emerald themes and OpenBox themes, but have also seen resources suggesting I can use GTK3 themes. But can I also install themes for qt apps separately?

So really:
Where can someone who has never explored themes in linux go to find basic information on how to use the different kinds of themes out there?

Thanks.
Hi! It looks like you know quite a bit about themes already!
Re. *But can I also install themes for qt apps separately?*, my guess is that you can install them but I feel you can have just one theme active at a time. 
So, ideally, if you want to run gtk2, gtk3, **and** qt apps in the same session, your best bet would be to find a theme that caters to all the apps you intend running. I feel you won't be able to run, in the same session, a gtk2 app with one theme and a gtk3 app with another theme and a qt app with a third theme.

(There's a [distro]("http://distrowatch.com/table.php?distribution=hybryde") that allows you to change DEs without logging out but that's OT.)

---

### Post by Adam's AI on 2012-08-31
> **vasa1 said:**
> Hi! It looks like you know quite a bit about themes already!
Re. *But can I also install themes for qt apps separately?*, my guess is that you can install them but I feel you can have just one theme active at a time. 
So, ideally, if you want to run gtk2, gtk3, **and** qt apps in the same session, your best bet would be to find a theme that caters to all the apps you intend running. I feel you won't be able to run, in the same session, a gtk2 app with one theme and a gtk3 app with another theme and a qt app with a third theme.

(There's a [distro]("http://distrowatch.com/table.php?distribution=hybryde") that allows you to change DEs without logging out but that's OT.)

Thanks for the reply. I know a little about themes, but think I have confused myself :P
That does look like an interesting distro, and I may give it a try. I'm still confused about how the themes interact though.

For the moment, just looking at Lubuntu, is it that OpenBox themes just affect window borders and GTK(2?) themes affect the window panels? But also Emerald themes can be used in that environment? What about running QT apps in that environment? I still don't really know and am curious if there are any websites that have some basic introductory information about themes.

---

### Post by Frogs Hair on 2012-08-31
> **Adam's AI said:**
> Thank you for the quick reply! I'm actually running Lubuntu as I mentioned, but I was wondering if there were general Linux theme-related info people could link me to, as it seems like multiple kinds of themes (beyond simply gnome 3.4) that will work on a given setup.

Sorry, I missed the L some how.;) Search for LXDE themes at the second link.

[http://box-look.org/](http://box-look.org/)

[http://xfce-look.org/](http://xfce-look.org/)

---

### Post by vasa1 on 2012-08-31
> **Adam's AI said:**
> ... if there are any websites that have some basic introductory information about themes.
You mean [like this one]("http://developer.gnome.org/gtk3/stable/theming.html")?

---

### Post by Adam's AI on 2012-08-31
> **Frogs Hair said:**
> Sorry, I missed the L some how.;) Search for LXDE themes at the second link.

[http://box-look.org/](http://box-look.org/)

[http://xfce-look.org/](http://xfce-look.org/)

Very interesting sites, thanks. Hmmm, there don't seem to be "LXDE themes" there, only GTK1, GTK2, and XFCE themes.

I've taken a look at the themes section of [http://opendesktop.org/?xsection=art](http://opendesktop.org/?xsection=art), but there were so many different theme types that I thought to start this thread, but it still seems like a big soup.

> **vasa1 said:**
> You mean [like this one]("http://developer.gnome.org/gtk3/stable/theming.html")?

That looks like a very detailed site! :) So, should I just be looking at GTK3? It appears that gtk2/3, emerald, possibly qt themes all work with LXDE?

---

### Post by Adam's AI on 2012-08-31
I'm going to play around with a few themes and see what I can get working and report back. Perhaps I'm not really framing my question clearly.

---

### Post by Adam's AI on 2012-09-05
Ok, I think I'm starting to understand how the different themes interact (and I've run into a problem).

:KSWhat I think I've learned:
Gtk2 themes affect the window panels in Lubuntu and can be added to a .themes folder in the user's home directory.

.obt Openbox themes affect window borders can be installed through the Customize Look & Feel panel.

Emerald themes are also for window borders (instead of Openbox themes) but require the emerald theming program which has been removed from the Ubuntu repositories for being 'in bad shape'.


:confused: I have run into **one problem** though:
I tried opening up some qt applications like Krita and Karbon to see how they look, and while they had menus according to the gtk2 theme, they had no window borders/decorations. I couldn't move or close them. **Any ideas on how to fix this ?**???
(When I opened them I anticipated having it work the other way around, gtk2 theme ignored, but borders working so this is a surprise).

---

### Post by black veils on 2012-09-05
(you can also apply panel background images, which theme the panel [http://xfce-look.org/usermanager/search.php?username=blackveils&action=contents](http://xfce-look.org/usermanager/search.php?username=blackveils&action=contents))

there are gtk2, gtk3, qt apps. if you have a theme, it will go in the .themes folder as you have discovered. in that theme folder, it will have subfolders for gtk2, gtk3 and qt ***if**  *the theme has support for them.

i am not sure how well integrated the default themes are in lubuntu/lxde, but if i were you i would stay with the default. you can tweak the colours sometimes, of those themes, using the appearance application. change the window decorations, wallpaper and panel backgrounds.

---

### Post by Adam's AI on 2012-09-05
> **black veils said:**
> (you can also apply panel background images, which theme the panel [http://xfce-look.org/usermanager/search.php?username=blackveils&action=contents](http://xfce-look.org/usermanager/search.php?username=blackveils&action=contents))

there are gtk2, gtk3, qt apps. if you have a theme, it will go in the .themes folder as you have discovered. in that theme folder, it will have subfolders for gtk2, gtk3 and qt ***if**  *the theme has support for them.

i am not sure how well integrated the default themes are in lubuntu/lxde, but if i were you i would stay with the default. you can tweak the colours sometimes, of those themes, using the appearance application. change the window decorations, wallpaper and panel backgrounds.

Thanks for the reply! I see, so gtk3 themes can work as well... I will give that a try.

Also, I installed qt4-qtconfig to try to fix my window-decoration-lacking qt apps issue. It lets me manually select a qt theme for my qt programs, but they are still borderless. Could it be an Openbox issue?

One more question: I got compiz to decorate the window by installing compiz, and compizconfig-settings-manager and enabling window decorations, but was wondering if people recommend adding the ppa/compiling emerald? I'm curious why it was removed from the official repos.

---

### Post by Frogs Hair on 2012-09-05
The Emerald project just died and the PPA was means to make Gnome 3 compatible and keep it alive for those still interested. I tried it on 9.10 and it didn't work consistently for me.

I had to use Cairo Dock with the Compiz fusion icon or it wouldn't start properly . I grew tiered of using the emerald --repace command just to see the theme at startup . I had to use the command if the dock wasn't in use. Others didn't and don't have this problem though.

---

### Post by Adam's AI on 2012-09-05
> **Frogs Hair said:**
> The Emerald project just died and the PPA was means to make Gnome 3 compatible and keep it alive for those still interested. I tried it on 9.10 and it didn't work consistently for me.

I had to use Cairo Dock with the Compiz fusion icon or it wouldn't start properly . I grew tiered of using the emerald --repace command just to see the theme at startup . I had to use the command if the dock wasn't in use. Others didn't and don't have this problem though.

That's unfortunate it died, some of the nicest themes I seem to find are emerald.

This might be a silly question, but I'm a bit of a noob and tend to stick to the official repositories. I've found instructions for installing it from source or from a ppa ([link]("http://ubuntuforums.org/showthread.php?t=1870792")), but is it safe to do so? (Again, noob disclaimer).

---

### Post by Frogs Hair on 2012-09-05
From what I can find _so far_ the Emerald 11.10 PPA was not updated for 12.04 and you may have to build it.

---

### Post by Adam's AI on 2012-09-05
> **Frogs Hair said:**
> From what I can find _so far_ the Emerald 11.10 PPA was not updated for 12.04 and you may have to build it.

Is there any way to know that it's virus free? Being a noob, I have stuck to the official repos since they are supposedly checked and safe.

---

### Post by vasa1 on 2012-09-06
> **Adam's AI said:**
> Is there any way to know that it's virus free? Being a noob, I have stuck to the official repos since they are supposedly checked and safe.
This particular issue will get a lot of attention, as it always does, when posted in the "Security" section of the forum ;)

---

