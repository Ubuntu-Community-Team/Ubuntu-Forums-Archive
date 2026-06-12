---
title: "change gtk-3.0 selected background in Adwaita theme"
date: 2012-09-22
forum: General Help
---

### Post by supernater on 2012-09-22
I wanted to edit the gtk-3.0 settings for the Adwaita theme.  I went to the gtk-3.0 folder and opened the gtk.css file and the only entry in it was..

```
@import url("resource:///org/gnome/adwaita/gtk-main.css");
```

I could not find where this file was located so I opened it from a command terminal using... 

```
gedit resource:///org/gnome/adwaita/gtk-main.css
```

However, I could not edit it and save it.  I tried copying the contents displayed in gedit to a new text file and saving that to the Adwaita gtk-3.0 folder but that did not work because when I reloaded Adwaita all gtk-3.0 apps had no theme colors at all.  All I want to do is change the background color of selected text in the Adwaita theme.  How do I do this?  Thanks.

---

### Post by vasa1 on 2012-09-22
Adwaita is a difficult thing to tweak, IMO. That's because it refers to a binary. For more details check out this blog: [http://funsurf-blog.blogspot.in/2012/06/building-binary-for-gtk3-theme.html](http://funsurf-blog.blogspot.in/2012/06/building-binary-for-gtk3-theme.html)
From what I've seen, the High Contrast theme, the inverse one, and Low Contrast, also make use of Adwaita's binary.

---

### Post by supernater on 2012-09-23
Thank you for the very useful link!  After reading that I can see that the resource file is the gtk.gresource file in the gtk-3.0 folder of the adwaita theme.  It looks like whoever made the theme put all the CSS files and PNG/SVG icon files in the gtk-3.0 directory.  Then they made an XML file that indexed all these files and ran the glib-compile-resources command.  After loading the Adwaita theme, I was able to extract the .css files from the resource file using the gedit commands I posted in my OP.  However I cannot extract the icon files from this resource.  I was hoping there was a way to do this but I was not able to figure it out.  Is there a way to completely "decompile" this to extract all the files?  If not then I guess I would have to find all of the theme files BEFORE they are compiled into a resource file.  Does anyone know where I can download the Adwaita theme before it's been compiled?  I went to gnome-look.org and xfce-look.org but could not find the theme.  When I did find variations of the theme, they were also compiled into a resource file.

---

### Post by vasa1 on 2012-09-23
I just don't use the Adwaita theme :(

Other themes work for me just as well and are totally "transparent".

---

### Post by vasa1 on 2012-09-23
My theme of choice is [Greybird]("http://shimmerproject.org/project/greybird/"). It's developers are accessible.

---

### Post by Darl181 on 2012-10-02
I think I might've figured out how to extract the gtk.gresource file. I'm using normal ubuntu, not xubuntu, so things may or may not be the same? I'm not sure about this..


I found something called gresource ( [http://developer.gnome.org/gio/2.32/gresource-tool.html](http://developer.gnome.org/gio/2.32/gresource-tool.html) ) which seems to be related.

I copied the Adwaita folder to ~/.themes (might not be necessary? idk, it's just easier to work with there imo) and in the terminal I ran this:
```
gresource list ~/.themes/Adwaita/gtk-3.0
```/gtk.gresource
And it listed out a bunch of png, svg and css files.

So, this..
```
gresource extract ~/.themes/Adwaita/gtk-3.0/gtk.gresource /org/gnome/adwaita/gtk-main.css
```..outputs what looks like css in the terminal. :)
Unfortunately doing the same for a png/svg seems to turn up raw data, and it doesn't seem to match the format for either.. :(
(some output pasted in [http://pastebin.com/f4Tg0nsW](http://pastebin.com/f4Tg0nsW) )

I'm not too familiar with ubuntu, but I'm thinking maybe some sort of script can be set up to just run down the list?


Anyway in reply to the first post, I think Gnome Color Chooser can change the background color for that. Much simpler :D

---

### Post by vasa1 on 2012-10-02
> **Darl181 said:**
> I think I might've figured out how to extract the gtk.gresource file. ...
...
My point remains ... why bother breaking one's head over Adwaita? Does it do something special that other themes don't? Of course, it's fine as an academic exercise.
> Anyway in reply to the first post, I think Gnome Color Chooser can change the background color for that. Much simpler
The Gnome Color Chooser is simpler but is restricted to gtk**2** apps and isn't useful for gtk**3** apps, AFAIK.

---

### Post by Darl181 on 2012-10-02
> **vasa1 said:**
> My point remains ... why bother breaking one's head over Adwaita? Does it do something special that other themes don't? Of course, it's fine as an academic exercise.
Not really, I guess..it just has some somewhat unique elements(the close buttons, the tabs). Though I'm guessing they could be duplicated anyway. Personally I wouldn't say no to being able to make Adwaita more the color scheme of MediterraneanNight or something..but yeah, there are plenty of alternatives which are easier to go around with.

> The Gnome Color Chooser is simpler but is restricted to gtk**2** apps and isn't useful for gtk**3** apps, AFAIK.I've only been using ubuntu for about a month, but in my experiences with 12.04 it's changed multiple gtk3 themes without having any evident problems..? Unless there's some underlying thing I'm not aware of, which could easily be the case.

---

### Post by vasa1 on 2012-10-02
> **Darl181 said:**
> ...
I've only been using ubuntu for about a month, but in my experiences with 12.04 it's changed multiple gtk3 themes without having any evident problems..? Unless there's some underlying thing I'm not aware of, which could easily be the case.
Could you mention the "gtk3" themes? If you look in your "gtk3" theme's folder, do you also see a gtk-2.0 folder? That means the gtk3 theme in question is actually a gtk2 and gtk3 theme.
Also, if you look in your home folder after enabling "view hidden files", you will see a .gtkrc-2.0 file. If you have installed GNOME Color Chooser, among the last lines in your .gtkrc-2.0 file will be a reference to GNOME Color Chooser.

---

### Post by Darl181 on 2012-10-02
> **vasa1 said:**
> Could you mention the "gtk3" themes? If you look in your "gtk3" theme's folder, do you also see a gtk-2.0 folder? That means the gtk3 theme in question is actually a gtk2 and gtk3 theme.
Also, if you look in your home folder after enabling "view hidden files", you will see a .gtkrc-2.0 file. If you have installed GNOME Color Chooser, among the last lines in your .gtkrc-2.0 file will be a reference to GNOME Color Chooser.Yeah, they have gtk-2.0 folders as well as those files at home. Idk, all I know is I click a color, stuff changes and it's good enough for me :P

Edit: the themes are Adwaita, MediterraneanNight and Ambiance-Colors.

Edit2: Related to Adwaita again found something that has it not-compiled :)
[https://launchpad.net/gnome-themes-standard](https://launchpad.net/gnome-themes-standard)
sudo apt-get source gnome-themes-standard

---

### Post by Draconicus on 2013-05-28
Alrighty, first and foremost, to get the PNGs out (with minor corruption  - maybe some kind of indexing header?), use > to pipe it to a file.  For example 

```

gresource extract ~/.themes/Adwaita/gtk-3.0/gtk.gresource/assets/slider.png > ~/.themes/Adwaita/gtk-3.0/assets/slider.png

```
In  that case it would be wise to make the folder first, and it would make  more sense to **move the active directory** (command line) to ** ~/.themes/Adwaita/gtk-3.0/** so you don't have to keep typing so much.
In  my experience with a different theme, it seems necessary open and  re-save the PNG with a simple image viewing program* (one capable of  saving - in my case, **gthumb**).*

Most well-made** gtk3.0** themes are  mainly using **CSS** to define objects. Only background patterns and unusual  shapes would require images. You should focus on **modifying the CSS** to  call for your background from somewhere else.

[B]Here's a step-by-step to free your theme from its resource file: 

0.  If you aren't using your [/B].themes folder**, you're doing it wrong.  Copy/install the theme to **~/.themes[B] and work in that directory. It's a  good idea to rename it too.
1. Use gresource to extract *all CSS  files*. Especially[/B] gtk-main.css** *(typically this file is the master, but  some themes are actually inventive, so pay attention to ****gtk.css*[B]*)*
2. Modify gtk.css to point to [/B]gtk-main.css** or whatever it uses: ** @import url("gtk-main.css");[B]
3.  Edit [/B]gtk-main.css**, where typically you'll find the base of the design  to be included in other css files later. If you can't find the thing you  want to modify, check for more** @import lines** for additional includes.**

Local  files will override the **gresource**, so you don't have to extract  anything other than the PNGs you need to change. You could even **create  new PNGs** in the appropriate folder (like **/assets** ) with the correct path  to override the resource data.
I'm currently using this to hack some  red into the **gtk3.0** side of a multi-platform theme I've fallen in love  with. I already redified the **gtk2.0** images via GIMP. Things like  scrollbars and buttons are **pure CSS** in the **gtk3.0** side.

---

