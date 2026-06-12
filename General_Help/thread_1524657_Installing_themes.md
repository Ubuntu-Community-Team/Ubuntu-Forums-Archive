---
title: "Installing themes"
date: 2010-07-05
forum: General Help
---

### Post by diego_pmc on 2010-07-05
I've been trying to install the [Hardy Mariux 2.0]("http://mariuxv.deviantart.com/art/Hardy-Theme-75628261") theme. I've installed Emerald Theme Manager and am trying to load one of the themes (Hardy 2.0 - Standard.emerald); I added it to Emerald, click it (which causes Emerald to close) then run [FONT=Lucida Console]emerald --replace[/FONT]. The bar at the top of the windows gets replaced, along with the buttons, but that all and the process running in the terminal never seems to end (it doesn't give any kind of output either).

Also, I'm most interested in the Mac OS X-like panel at the bottom of the screen and the bar at the top of the window that comes in the Hardy 2.0 - Standard package. What exactly do I have to install out of the whole package to get these two things working?

---

### Post by diego_pmc on 2010-07-05
(*bump*)

---

### Post by stinkeye on 2010-07-05
Emerald is a window decorator...eg border and title.(which you don't have to use..you can just choose a gtk decorator in
Appearance > theme > customize > window border.)

In your download goto the gtk folder and drag and drop the folder named 
Hardy-Mariux 2.0 into the system > preferences > Appearance window.
The gtk theme will change your window colours and style.

To install your icons goto the icons folder in your download and drag and drop *Tangerine.tar.gz * into the Appearance window.

To change the top panel look at the readme in your download.
The dock is avant-window-navigator ... search for it in the software centre.

A properly made gtk2 theme should change the panel background, the window border and title, and the style and color
by just dropping in Appearance.
Some people prefer to use emerald as the window border because it's more customizable...eg border thickness and transparency.

Have a look here for more gtk2 themes [**_gnome-look_**]("http://gnome-look.org/")

---

### Post by marin123 on 2010-07-05
i use Docky as a dock and its very good, if you want to, try it out...

---

### Post by diego_pmc on 2010-07-05
Oohhh, I though those panels were part of the actual Desktop, not separate applications. Oh well, it doesn't really matter. I think I'll stick with Docky -- it seems to be more fluid (less resource demanding?).

Now I would like to remove the bottom panel (I know I can do that by right-clicking then selecting "Delete This Panel"). My question is, how can I move the workplace and recycle bin "icons" onto Docky? Also, how about the button that minimizes all active windows?

And for future reference, how would I go about restoring the bottom panel? Will it restore itself the way it is now (minimize-all button + workplaces + recycle bin)?

EDIT: Or maybe you can suggest a better way to reorganize those icons. :)

---

### Post by stinkeye on 2010-07-05
In docky preferences there are docklets for "show desktop" and recycle bin.
No workspace switcher though.
You may have to add the docky ppa for a more recent version of docky for these docklets
To add the PPA run the following in a terminal: -
```
sudo add-apt-repository ppa:docky-core/stable
sudo apt-get update && sudo apt-get install docky
```


If you remove the bottom panel you lose all the applets.
You can add them back by right clicking on the new panel and selecting "add to panel".

---

### Post by diego_pmc on 2010-07-05
Okay, thanks a lot. I love my new GUI. :D

---

### Post by stinkeye on 2010-07-05
> **diego_pmc said:**
> Okay, thanks a lot. I love my new GUI. :D
Well post a pic then. ;)

---

### Post by diego_pmc on 2010-07-07
Sure thing: [http://img686.imageshack.us/f/screenshotuoe.png/](http://img686.imageshack.us/f/screenshotuoe.png/)
Kinda empty for now (fresh installation), but I like the look.

---

### Post by stinkeye on 2010-07-07
> **diego_pmc said:**
> Sure thing: [http://img686.imageshack.us/f/screenshotuoe.png/](http://img686.imageshack.us/f/screenshotuoe.png/)
Kinda empty for now (fresh installation), but I like the look.

All you need now is conky, to put a little bit of pizzazz on that clean desktop.
Beware conky is addictive! ;)
[**_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

---

