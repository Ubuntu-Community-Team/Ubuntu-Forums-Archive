---
title: "Edit Netbook Remix Launcher Icons"
date: 2009-08-27
forum: General Help
---

### Post by brandoncolorado on 2009-08-27
I am using Karmic Netbook Remix.  I added a website as a favorite icon with the heart icon in Firefox.  The icon added to my favorites tab in launcher.

How can I make the icon match the favicon of the site?  Right now all websites show as a generic icon.  Also, how can I edit the name under the icon?

---

### Post by beastrace91 on 2009-08-27
Preferences->Edit Menus

~Jeff

---

### Post by brandoncolorado on 2009-08-27
> **beastrace91 said:**
> Preferences->Edit Menus

~Jeff

Do you mean System--->Main Menu?  I couldn't find a preferences button or an "edit menu" button.

---

### Post by beastrace91 on 2009-08-27
Ahh yes, main menu. Sorry I was not looking at the menu when I posted and thought it was labeled edit menus.

~Jeff

---

### Post by brandoncolorado on 2009-08-27
> **beastrace91 said:**
> Ahh yes, main menu. Sorry I was not looking at the menu when I posted and thought it was labeled edit menus.

~Jeff

I do see that menu now.  There is a "favorites" section there, but there is nothing in it.  However, I have saved things to my favorites and they do show up on the favorites tab in the netbook launcher.

---

### Post by brandoncolorado on 2009-08-30
*bump*

---

### Post by kerry_s on 2009-08-30
i don't know if karmic is like jaunty, i haven't been able to use karmic it always freezes right at the desktop.

anyways in jaunty the icons *.desktop files are kept in ~/.local/share/applications

you can go in there and edit it, use the editors file-> open function, look for "Icon=exec" or something like that & just point it where you want.

---

### Post by Napu5 on 2009-10-24
I think it is caused by this bug:
[https://bugs.launchpad.net/ubuntu/+source/netbook-launcher/+bug/424822](https://bugs.launchpad.net/ubuntu/+source/netbook-launcher/+bug/424822)

---

### Post by blokeley on 2009-11-07
You can rearrange the list by editing
~/.gconf/apps/netbook-launcher/favorites/%gconf.xml

---

