---
title: "Xfce menu/launcher questions"
date: 2011-05-07
forum: General Help
---

### Post by The Cog on 2011-05-07
I want to add a custom launcher to Xubuntu (xfce version 4.8.3). Two seaparate questions:

1: 
I can add a launcher to a panel, but how can I change the icon to one of my choosing? It seems to only offer a predetermined set of icons, not an "open file" dialog.

2:
How can I edit the menu to add new items? The xfce web site says they tested with alacarte, but apt-get alacarte wants to install loads of other stuff that I don't want. It even wants to install evolution - as a dependency of a menu editor??? They're 'avin' a larf!

---

### Post by ajgreeny on 2011-05-07
Have you tried installing alacarte without all the recommended packages?  You can do that from the preferences of synaptic, in the first tab, (General, I think) or you can with apt-get using the option **--no-install-recommends**.

I have no idea if this will make the difference you want, but it's worth a try.

---

### Post by The Cog on 2011-05-07
> Have you tried installing alacarte without all the recommended packages? You can do that from the preferences of synaptic, in the first tab, (General, I think) or you can with apt-get using the option --no-install-recommends.Excellent! It seems I should RTFM more often. That did the trick, thank you. I'll get on with playing with it now.

---

### Post by The Cog on 2011-05-07
OK, two steps forward, one step back.

I can add icons to the set that xfce offers by copying a png to /usr/share/icons.

alacarte seems broken though. It seems to have gnome-panel as an actual dependency, which again drags in lots of stuff I don't want. So I still don't have a way to edit menus. Any help would be appreciated.

---

### Post by Jose Catre-Vandis on 2011-05-07
1. When you go click on the icon button in the launcher, one of the choices is "Image Files". This allows you to browse your PC for the image you want to use. Suggest you keep your own images down to 48x48 pixels though :)

2. A quick fix for the right click and Application menu is to turn off the desktop icons (Settings > Desktop > Icons > Icon type = None). But alacarte is the preferred way of further editing. I've not bothered though....;)

---

### Post by The Cog on 2011-05-07
> **Jose Catre-Vandis said:**
> 1. When you go click on the icon button in the launcher, one of the choices is "Image Files". This allows you to browse your PC for the image you want to use. Suggest you keep your own images down to 48x48 pixels though :)That's embarassing - I should have spotted that. Thank you.> 
2. A quick fix for the right click and Application menu is to turn off the desktop icons (Settings > Desktop > Icons > Icon type = None).I'm not sure what you mean there. What is that meant to fix?

---

### Post by Jose Catre-Vandis on 2011-05-08
> **The Cog said:**
> That's embarassing - I should have spotted that. Thank you.I'm not sure what you mean there. What is that meant to fix?

It turns off the first big list with all the "unnecessary" stuff in the menu and just leaves you with the applications for the right click menu:

[ATTACH]191547[/ATTACH]

[ATTACH]191548[/ATTACH]

I don't bother editing further as it gives me access to all apps installed, I use the dock (these pics from 10.10 so using wbar) for most used apps

---

### Post by The Cog on 2011-05-08
Ah yes, I see what you mean, thank you.

That's an impressive array of launchers you have there.

---

### Post by Jose Catre-Vandis on 2011-05-08
I'm a busy boy :)

Here's where I am at with Xubuntu 11.04

[http://ubuntuforums.org/attachment.php?attachmentid=191255&d=1304625843](http://ubuntuforums.org/attachment.php?attachmentid=191255&d=1304625843)

[http://ubuntuforums.org/attachment.php?attachmentid=191256&d=1304625876](http://ubuntuforums.org/attachment.php?attachmentid=191256&d=1304625876)

---

