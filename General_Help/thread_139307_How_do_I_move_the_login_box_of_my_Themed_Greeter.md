---
title: "How do I move the login box of my Themed Greeter?"
date: 2006-03-03
forum: General Help
---

### Post by ryan76 on 2006-03-03
I'm trying to move the login box only of my theme, Earthlights.

I found this in Earthlights.xml:

```
<!-- password box -->
-
	<item type="rect">
<pos x="50%" y="66%" width="box" height="box" anchor="c"/>
```

This file is inside the tar.gz file though - I never extracted it to install it, I just installed it through the System menu.

Is this the right way to move the login box? How would I change it since I don't know where it installed?

Many thanks for any help

---

### Post by majikstreet on 2006-03-03
I don't know how you'd change it, but that sounds right. 
But, I do know where GDM themes are installed. And that is at
```

/usr/share/gdm/themes

```
It'll be in a folder with a name similar to the name of the theme..

Also, you have to use sudo to edit it.. So you can do sudo gedit whatever.. For a theme that I use, called GreenGDM, this is what I would do:
cd /usr/share/themes
ls
and check for greengdm, then cd into the folder with that name
cd GreenGDM
sudo gedit green_gdm.xml

then I can change stuff..

Hope that helped,
majikstreet

---

