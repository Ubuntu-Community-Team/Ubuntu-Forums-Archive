---
title: "Mac EyeCandy HelP? Icons &amp; Macbar"
date: 2009-07-18
forum: General Help
---

### Post by Codix121 on 2009-07-18
So, I downloaded this FULL PACKAGE of OSX stuff,
i got the login, theme, etc working fine.
I just need help on a few things,
I'm still very new to ubuntu, so I'm wondering,

How Do I Install Icons? I have it in tar.gz format.
also I have this thing called a MACBAR, well it's a folder,
and it contains a .sh file but I tried running it but nothing happened,
Anyknow how I can get my topbar to look like mac or how to change it?

would appreciate it, and also my screenlets don't work,
I made a folder in my home called .screenlets and put in the folder of the screenlet on their but no luck.

I like ubuntu so far, it's much better than windows,
but if only I could get it to look like I want it.

Oh and Xcursors doesn't seem to work either,
whenever I click INSTALL NEW THEME, nothing opens :(

Thank you,
Jorge.

---

### Post by CatKiller on 2009-07-18
> **Codix121 said:**
> How Do I Install Icons?

System &#8594; Preferences &#8594; Appearance. Drag and drop your archive onto the window.

Or extract your archive to ~/.icons.

---

### Post by cabrey on 2009-07-18
To activate the newly installed icon theme, go to the aforementioned 'Appearance' panel and click 'Customize...' and go to the 'Icons' tab. Select the icon theme you just installed and you are done.

PS, if you want to have a Mac's functionality, you will need a dock. And for that, I recommend GNOME-Do's Docky. :D

---

### Post by CaptainEvilStomper on 2009-07-18
Make sure you have the Screenlets daemon installed and running. Open a Terminal window and type this:

```
sudo apt-get install screenlets
```
Then run Screenlets (I think it's in Applications > Accessories but I might be wrong). Once Screenlets is running, just click Install over on the left side, click OK, and find the screenlet you want to install.

As for the menu bar, it depends on whether you want an actual working menu bar or you just want the top panel to look like the Mac menu bar. To change the appearance, right-click on any space not occupied by an applet, click Properties, and resize it to 25 pixels. Then click Background, click Background Image, and click the button underneath that and find the image you want to use. You can use this image for a solid menu bar ( [http://img139.imageshack.us/img139/9559/panelbgsolidblackline.png](http://img139.imageshack.us/img139/9559/panelbgsolidblackline.png) ) and this one for a transparent menu bar ( [http://img36.imageshack.us/img36/5492/panelbgtransblackline.png](http://img36.imageshack.us/img36/5492/panelbgtransblackline.png) ).

To get a global menu bar like in OS X, install the Gnome Global Menu Bar ( [http://code.google.com/p/gnome2-globalmenu/](http://code.google.com/p/gnome2-globalmenu/) ). The 64-bit version causes some apps to crash (notably Firefox and Songbird), but if you're using a 32-bit version of Ubuntu you shouldn't have any problems.

Also, if you can't manage to get the theme you're using to work, you might want to try Mac4Lin instead: [http://sourceforge.net/projects/mac4lin/](http://sourceforge.net/projects/mac4lin/) And I agree with cabrey - Gnome-Do is definitely the way to go. When you use Docky as the theme you basically get the Dock plus Spotlight in one application, except Gnome-Do can be configured to do a lot of things Spotlight can't (like run Terminal commands or search for a location on Google Maps).

---

