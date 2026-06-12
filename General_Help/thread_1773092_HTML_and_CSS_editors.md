---
title: "HTML and CSS editors"
date: 2011-06-01
forum: General Help
---

### Post by highonpop on 2011-06-01
I'm looking for a good HTML/CSS editor. I'm currently taking web design classes and this is mandatory to have.

I had been using notepad++ and my professor had been using Text Wrangler. Is there a linux version for these? Or a comparable program? Preferably with color coding like np++ and TW.


If not, can np++ be installed and operated on wine?

---

### Post by SeijiSensei on 2011-06-01
If you want context-highlighting, most native Linux editors will do that for you automatically.  Both gedit (on GNOME) and kate (on KDE) do this, as do text-based editors like emacs or my favorite, [jed]("http://www.jedsoft.org/jed/").

---

### Post by linuxinstalledfromhdd on 2011-06-01
> **highonpop said:**
> I'm looking for a good HTML/CSS editor. I'm currently taking web design classes and this is mandatory to have.

I had been using notepad++ and my professor had been using Text Wrangler. Is there a linux version for these? Or a comparable program? Preferably with color coding like np++ and TW.


If not, can np++ be installed and operated on wine?

I use notepad++ but it is almost impossible to port that over to run natively in Linux.

However, here is a good way to get it running in Ubuntu:

[http://cinderbox.net/2011/05/18/how-to-install-notepad-in-ubuntu-with-wine/](http://cinderbox.net/2011/05/18/how-to-install-notepad-in-ubuntu-with-wine/)

It's really the only one I use for programming.

---

### Post by highonpop on 2011-06-01
will the native's recognize css and html? and color code accordingly, or do i just have to know its css and html?

with np++ and tw i can save as a .css or .html, re-open with the text color coded and formatted according to which type of code you are typing. np++ and tw will highlight both the opening and closing tags for you in all different colors depending on the type of code, ad well as giving a testing feature allowing you to open the code you are typing in several different browsers at once.

---

### Post by ruffEdgz on 2011-06-01
I have not found any GUI based editors that I love so I still use my favorite editor on the command line:
```

vim

```
Other GUI editors that I found for linux but are ok would be:
[LIST]
[*]Bluefish
[*]KompoZer
[*]Quanta
[*]Mozilla Seamonkey
[/LIST]
These apps were found from the repo but there are other editors you can look at on this website: [http://www.dmoz.org/Computers/Software/Internet/Authoring/HTML/WYSIWYG_Editors/](http://www.dmoz.org/Computers/Software/Internet/Authoring/HTML/WYSIWYG_Editors/)

---

### Post by highonpop on 2011-06-01
> **linuxinstalledfromhdd said:**
> I use notepad++ but it is almost impossible to port that over to run natively in Linux.

However, here is a good way to get it running in Ubuntu:

[http://cinderbox.net/2011/05/18/how-to-install-notepad-in-ubuntu-with-wine/](http://cinderbox.net/2011/05/18/how-to-install-notepad-in-ubuntu-with-wine/)

It's really the only one I use for programming.


Thank You!

---

### Post by seawolf167 on 2011-06-01
I love Geany for coding

```
sudo apt-get install geany
```

---

### Post by mcduck on 2011-06-01
> **highonpop said:**
> will the native's recognize css and html? and color code accordingly, or do i just have to know its css and html?

with np++ and tw i can save as a .css or .html, re-open with the text color coded and formatted according to which type of code you are typing. np++ and tw will highlight both the opening and closing tags for you in all different colors depending on the type of code, ad well as giving a testing feature allowing you to open the code you are typing in several different browsers at once.

Yes, pretty much any Linux text editor will support syntax highlighting for HTML and CSS, and a huge list of other file types.

I'd recommend the editor that comes with Ubuntu, Gedit. It sure is a lot more powerful that what you'd expect the default editor on an OS to be, and has a great plugin system for adding new tools and features.

(seriously, at some point I had project management tools, file manager, terminal, web browser and music player running inside Gedit, just because a friend of mine complained that it was just like the useless windows Notepad and had no features. :D. Currently I'm running pretty light-weight, with just a few simple default plugins and the awesome [zen-coding]("http://code.google.com/p/zen-coding/") plugin enabled.)

---

### Post by linuxinstalledfromhdd on 2011-06-01
> **mcduck said:**
> Yes, pretty much any Linux text editor will support syntax highlighting for HTML and CSS, and a huge list of other file types.

I'd recommend the editor that comes with Ubuntu, Gedit. It sure is a lot more powerful that what you'd expect the default editor on an OS to be, and has a great plugin system for adding new tools and features.

(seriously, at some point I had project management tools, file manager, terminal, web browser and music player running inside Gedit, just because a friend of mine complained that it was just like the useless windows Notepad and had no features. :D. Currently I'm running pretty light-weight, with just a few simple default plugins and the awesome [zen-coding]("http://code.google.com/p/zen-coding/") plugin enabled.)

The latest version of Notepad++ works terrific in Wine. If they want notepad++, that's the best way.  Just always always make sure to do plenty of backups while working with it, since it is running in Wine.  That's my advice to anyone who is going to use Notepad++ in wine on Ubuntu.  :)

And another trick that I use for programming in Ubuntu is Virtualbox 4 and Visual Studio in WinXP.  You can even test your work natively, which is great too.

---

### Post by WorMzy on 2011-06-01
Gedit is a great editor if you're looking for something simple. Personally, I use vim. It's a much much more powerful editor than gedit, but consequently has a much steeper learning curve while getting used to it. Once you've learnt how to use it, you'll be able to write code a damn sight faster than you can in "normal" text editors.

---

### Post by derklempner on 2011-06-01
I'm surprised nobody's mentioned [[COLOR="Red"]_Amaya_[/COLOR]]("http://www.w3.org/Amaya/"), which was specifically started as an HTML and CSS style sheets editor.

---

### Post by linuxinstalledfromhdd on 2011-06-01
Cool. I'm going to download it and give it a spin. :) Thanks.:popcorn:

---

