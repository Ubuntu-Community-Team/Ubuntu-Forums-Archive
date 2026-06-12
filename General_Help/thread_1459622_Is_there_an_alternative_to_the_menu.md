---
title: "Is there an alternative to the menu?"
date: 2010-04-21
forum: General Help
---

### Post by HHx66 on 2010-04-21
I recently installed xfce alongside kde on kubuntu, I really like how fast it is, but can't stand the menu. Is there a way to add a KDE4 style menu to it? The only thing I really miss is I have a lot of programs and I miss the favorites, and the search function built in. So any plugins or anything I can do to make it more like that?

---

### Post by -humanaut- on 2010-04-21
Xfce's panels are extermely customizable you can virtually do anything to them go xfce.com and go there wiki theres a lot about .gtkrc-2.0 files that you can edit

---

### Post by MadCookie on 2010-04-21
> **HHx66 said:**
> I recently installed XFCE alongside KDE on Kubuntu, I really like how fast it is, but can't stand the menu. Is there a way to add a KDE4 style menu to it? The only thing I really miss is I have a lot of programs and I miss the favorites, and the search function built in. So any plugins or anything I can do to make it more like that?

XFCE is designed to be as light as possible, and that is maybe why they have that kind of menu. You could always run KDE-plasma in XFCE, but it will give you the feeling running KDE, and it will definitely slow everything down as well.

It does not yet exist any "xfce-goodie" that gives you a KDE-like menu in xfce, you can try by running
```
plasma
```
or
```
plasma-desktop
```
in the run dialog that opens when you press Alt + F2 in XFCE.

NOTE: I am not sure if either of the commands are correct.

---

### Post by HHx66 on 2010-04-21
I found a program called GnoMenu, it's a gnome panel item, I heard you can run it on XfApplet (here: [http://goodies.xfce.org/projects/panel-plugins/xfce4-xfapplet-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-xfapplet-plugin)) how would I install that?

---

### Post by ajgreeny on 2010-04-21
You can also add certain versions of the Linux Mint menu to ubuntu, and maybe xubuntu as well.  Search around to see if you can find any info on that in xubuntu, Certainly for jaunty you could add mintsystem and mintmenu, but I think it was the versions of mint packages from mint 6, not mint 7.  I have no idea about doing this in karmic, so you may need to search a bit.

---

### Post by waynefoutz on 2010-04-21
Mint uses gnome-main-menu just install that package with synaptic. 

[IMG]http://reverendted.files.wordpress.com/2007/02/main-menu-video-screenshot.png?w=536&h=405[/IMG]

to get the effect above, delete the lower panel, bring the top panel down to the bottom, add gnome-main-menu and the task switcher app.

---

### Post by -humanaut- on 2010-04-21
You can alter the Xfce menu in virtually anyway imaginable you just have to be comfortable with editing text files.

---

### Post by -humanaut- on 2010-04-21
> **waynefoutz said:**
> Mint uses gnome-main-menu just install that package with synaptic. 

[IMG]http://reverendted.files.wordpress.com/2007/02/main-menu-video-screenshot.png?w=536&h=405[/IMG]

to get the effect above, delete the lower panel, bring the top panel down to the bottom, add gnome-main-menu and the task switcher app.

Bringing that amount of Gnome Dependencies defeats the purpose of Xfce.

---

### Post by x1a4 on 2010-04-21
> **HHx66 said:**
> I found a program called GnoMenu, it's a gnome panel item, I 
heard you can run it on XfApplet (here: [http://goodies.xfce.org/projects/panel-plugins/xfce4-xfapplet-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-xfapplet-plugin)) how would I install that?

Install the **xfce4-xfapplet-plugin** package using Synaptic or from a terminal: ```
sudo apt-get install xfce4-xfapplet-plugin
```

r-Click a panel > 'Add new item' and add the XfApplet applet to a panel then edit its properties to add a Gnome panel applet.  The XfApplet properties window will open automatically once you add the applet to the panel.  Later just r-Click the applet and select it's properties which will be under the menu items of the Gnome applet inside Xfapplet.  Obviously you have to have GnoMenu installed first before you can use it.

---

### Post by kerry_s on 2010-04-21
+1 xfapplet + gnome-main-menu


> Bringing that amount of Gnome Dependencies defeats the purpose of Xfce.

less then 6mb really ain't a whole lot of gnome.

---

### Post by x1a4 on 2010-04-21
> **MadCookie said:**
> XFCE is designed to be as light as possible, and that is maybe why they have that kind of menu.
Nope.  A couple years back I read on the Xfce list that the menu sucks as much as it does is because no one has the time to do any real work on it.  It's actually not finished yet.  Plans are to improve the menu in v5, but considering other priorities it may not happen, unless somebody volunteers and contributes some code.  Any takers? :)

---

### Post by HHx66 on 2010-04-21
So far none of those solutions really work. gnome-main-menu won't load right and GnoMenu doesn't work at all. Any other suggestions? I'd even settle with just a way to be able to search through the programs to launch them.

---

### Post by -humanaut- on 2010-04-21
> **HHx66 said:**
> So far none of those solutions really work. gnome-main-menu won't load right and GnoMenu doesn't work at all. Any other suggestions? I'd even settle with just a way to be able to search through the programs to launch them.

You need to edit the .gtkrc-2.0 file here's a website to help you out. [http://xfce-look.org/content/show.php/gtkrc-2.0+Panel+Colour+Changer?content=83538](http://xfce-look.org/content/show.php/gtkrc-2.0+Panel+Colour+Changer?content=83538)

---

### Post by kerry_s on 2010-04-21
> **HHx66 said:**
> So far none of those solutions really work. gnome-main-menu won't load right and GnoMenu doesn't work at all. Any other suggestions? I'd even settle with just a way to be able to search through the programs to launch them.

what do you mean "won't load right"?
is it just you've never used it before?

did a lot of pics have to split 1 to the next post.

---

### Post by kerry_s on 2010-04-21
last pic.

anyways after that it's just a matter of changing the gnome parts to call xfce4 stuff, the logout you just need to change the command in /usr/share/applications. system monitor, just install the gnome one it's better.

---

### Post by kerry_s on 2010-04-22
so anyway's after a couple of minutes of messing around, mine looks like this.

edit: you can change the system monitor in gconf-editor, you'll also need to set the file manager to thunar in there. for the search install catfish & set that in gconf-editor.

---

### Post by HHx66 on 2010-04-22
I got it to look like that, however, it only gives me the option for "More documents" and no program list at all.

---

### Post by kerry_s on 2010-04-22
> **HHx66 said:**
> I got it to look like that, however, it only gives me the option for "More documents" and no program list at all.

you got to add some programs for it to show, thats why the first thing is to click on the more applications & drag & drop what you want on the menu icon.

anyways done playing with it, i'm in the process of removing it, i'm fine with the standard boring menu. :lolflag:

---

### Post by HHx66 on 2010-04-22
Alright, I'll try that when I get some time.

---

### Post by HHx66 on 2010-04-22
Alright, I got it working. But where exactly do I change the command for logout?

*edit*

I actually need help with gconf-editor as well (like what commands and where they are at, etc) so any help would be greatly appreciated. Thanks for all the replies so far to everyone.

*edit again*

Nevermind, I managed to get it working perfectly, thanks for all the help and this was pretty much exactly what I was looking for. I appreciate all the help from the users on these forums.

---

