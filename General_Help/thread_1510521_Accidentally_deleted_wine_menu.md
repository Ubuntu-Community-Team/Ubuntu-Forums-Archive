---
title: "Accidentally deleted wine menu"
date: 2010-06-15
forum: General Help
---

### Post by frt975 on 2010-06-15
I accidentally deleted the wine menu 9.10. What I like to do when I install a new version of Ubuntu is have home on a separate partition and then do a fresh install. When I installed 10.4 also I reinstalled wine 1.2 and the menu hasn't come back. How do I get it back?

---

### Post by frt975 on 2010-06-23
Bump

---

### Post by Noz3001 on 2010-06-23
Right click and Edit Menus. Is it in there?

---

### Post by frt975 on 2010-06-23
It's not there.

---

### Post by elliotn on 2010-06-23
Reinstall wine

---

### Post by frt975 on 2010-06-23
I already did that but I did it again and the menu still isn't there. I have multiple accounts and mine is the only that has the wine menu missing. Is there some file I can copy and paste to get the menu back?

---

### Post by frt975 on 2010-06-25
bump

---

### Post by JoeGoalie on 2010-07-20
Did the same thing... Also, looking for how to get the menu back.

---

### Post by mc4man on 2010-07-20
Try 
```
gedit ~/.config/menus/applications.menu
```

look down and if you see this section about wine, if so, then remove only what I've  highlighted in red and save



```
<Menu>
		<Name>wine-wine</Name>
		<DirectoryDir>/home/doug/.local/share/desktop-directories</DirectoryDir>
		[COLOR="Red"]<Deleted/>[/COLOR]
	</Menu>
</Menu>
```

Then try your Applications menu , if still not there then go in terminal
```
alacarte 
```
and see if it's there in r. side to enable

---

### Post by frt975 on 2010-07-21
Thanks! That works perfectly except mine is just a little different:```
<Menu>
        <Name>wine-wine</Name>
     [COLOR=Silver]   <DirectoryDir>/home/doug/.local/share/desktop-directories</DirectoryDir>[/COLOR]
        <Deleted/>
    </Menu>
[COLOR=Silver]</Menu>[/COLOR]

 
```

---

### Post by shawnlauzon on 2010-11-16
Thanks for the post about <Deleted/>, that helps me too.

---

### Post by Freyrson on 2011-02-12
I have the same problem but the gedit solution that you guys came up with isn't working. I only started using Kubuntu in the last week, so if you could explain it like to an idiot I'd appreciate it. This is what I get when I try to use gedit and I have no idea what it means. I already tried to uninstall and reinstall wine so, yeah. Help!

```
**  (gedit:21538): WARNING **: Could not load theme icon gtk-home: Icon 'gtk-home' not present in theme

(gedit:21538): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
```

---

### Post by davidorourke on 2012-07-01
Thanks, that worked great. I deleted mine on purpose to get rid of Dreamweaver but wouldn't delete or uninstall, so deleted all of wine, reinstalled wine, but never saw the menu for wine anymore. So thanks, this helped get it back. Awesome help you guys.:D

---

