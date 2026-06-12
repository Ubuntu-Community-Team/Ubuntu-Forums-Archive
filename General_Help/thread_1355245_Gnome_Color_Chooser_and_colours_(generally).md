---
title: "Gnome Color Chooser and colours (generally)"
date: 2009-12-14
forum: General Help
---

### Post by zcacogp on 2009-12-14
Chaps, 

I'm not sure if there is an easy answer to this, but I am playing around with Gnome Color Chooser (GCC) and colours more generally, and I am a little confused as to what is referred to by what title, and what is set in the theme. 

For instance, I can set the colour (or pattern) of the top menu panel (the one with "Applications", "Places" and "System" in it) by changing it under "Panel" in GCC, OR by changing the colour in the File Browser ("Edit" > "Backgrounds and Emblems" and choose a colour or pattern), OR by right-clicking on the panel and choosing "Properties" and the "Background" tab). 

BUT only some things on the panel change - some things (like the background to the screen brightness icon) can be independently changed under "Global Colors" > "Normal" > "Background" in GCC. 

ALSO, it seems that if you use some themes, these set the colours of the panels by themselves, and they can't then be over-ridden. Ditto with the colours of the pop-up menus (which appear when you click on the "Applications", "Places" or "System" buttons on the top panel). Some themes allow you to change the colours of these, and the highlights on these, and some don't. 

Is there a good on-line instruction set, or (even better) tutorial on setting colours in Gnome? I have a bit of a vision of how I would like my desktop to look, but don't know where to reach to find the tools to accomplish it. (I'd like to play with transparency as well, but appreciate that this may be a stage or two more complex ... )

Also, given that some themes seem to hard-code some colours, which theme is the 'basic' one, which then allows you to change anything and everything? (Is this related to the "Engines" tab in GCC? What does this mean? What does this do?) 

Thanks, in advance, for any help. 


Oli.

---

### Post by zcacogp on 2009-12-15
Anyone? ... bumpitty-bump ...


Oli.

---

### Post by stinkeye on 2009-12-15
I don't fully understand how gtk themes work but all the info is found in the ~/.themes > theme folder > gtkrc
Could also be in /usr/share/themes if you installed the theme as root.
In the panel preferences you can choose to use background from the current theme, solid colour or custom image.
On some themes if you choose to use a solid colour for the panel, the themes background still shows behind the applets.
Solution...go into the theme folder and rename or delete the panel background png.
Would be better to use the gtkrc file if you know how to do it.
In some of my themes I've swapped the panel background image for one from another theme or gimped it to change the colour.
Also used a colour picker to grab a colour from the nautilus window and then searched for that colour in the gtkrc file to change it.
[_[COLOR="DarkRed"]GTK Theming Tutorial[/COLOR]_]("http://live.gnome.org/GnomeArt/Tutorials/GtkThemes")

---

### Post by JackTheDipper on 2009-12-15
A good theme for customizing is the default one, Clearlooks.
Pixmap/Pixbuf themes use images instead of color parameters, so their colors cannot be changed easily.

---

### Post by zcacogp on 2010-01-09
Chaps, 

Thanks ... I'll go and explore ... 


Oli.

---

