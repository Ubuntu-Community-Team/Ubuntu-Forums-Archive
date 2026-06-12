---
title: "same look (icons, background...) for all users."
date: 2006-03-06
forum: General Help
---

### Post by tioneb on 2006-03-06
Hi,

I've just installed ubuntu on a professional desktop, and I'd like that all users have the same look of their work space (icons, metafile, background...) but not the original one.
So I've done what I wanted on my session.
Now, I don't know where are the defauts values to apply what I have to the others users.

thanks

---

### Post by Xian on 2006-03-06
I would just move the hidden gnome config files in your own home directory to any other machine that you wish to have the same look and feel, in essence replacing the ones present on that particular system.

The files/folders you want to transfer are:
The '*' designates all similar names....

.gconf*
.gnome*
.config
.metacity
.nautilus
.mozilla
.gtkrc*

And in addition (if present):
.fonts
.themes
.icons

---

### Post by tioneb on 2006-03-08
the fact is that if I simply transfer that, me and the others will have the same look even I modify mine because all the link in these files are on /home/me....
Actually I'd like to know where does gnome take its information when it creates a new account, then I'd be able to change it and apply a different 'default' themes or configuration for gnome

but thanks anyway ;)

---

### Post by kaamos on 2006-03-08
I think you can put stuff in /etc/skel and it is copied to the home directory when a new user is created.

---

### Post by tioneb on 2006-03-08
I'll try and it sounds good :D but I don't know how to start :(

Mine just contains both config files for the bash that's all... so if a create a .gnome folder and his friends they would be erased by the ones created by gnome itself, don't they ????

thanks

---

### Post by tioneb on 2006-03-08
I found the folder /etc/gconf/gconf.xml.defaults/
it looks closer to what I'd like to do, does anybody know something about before I make shit :)

---

### Post by tioneb on 2006-03-15
Actually, go to the gnome web page -> download the documentation and everything is in !!! Such a good doc !!
by the way:
/etc/gconf/*mandatory* for unmodified parameters
/etc/gconf/*default* for default paramters
everything is in xml :)

---

### Post by mannheim on 2006-03-15
You can actually use the gui application gconf-editor to do this, if you prefer. Start gconf-editor with root permissions:
```

sudo gconf-editor

```
then, in gconf-editor, go to File-->New Defaults Window. Then edit the settings in the new gconf window. You will be editing the default settings. You can also edit the mandatory settings in the same way (another item in the File menu).

---

### Post by tioneb on 2006-03-15
Yep that's easier and more useful sometimes :)
thank's

---

