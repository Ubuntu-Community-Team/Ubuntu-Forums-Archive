---
title: "change mouse size"
date: 2012-10-05
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-10-05
i changed it here but the mouse keep changing back and forth to and from 24 seemingly at random (loading page in ff or while over panel)

---

### Post by vasa1 on 2012-10-05
> **pqwoerituytrueiwoq said:**
> i changed it here but the mouse keep changing back and forth to and from 24 seemingly at random (loading page in ff or while over panel)

Some resources:
[http://ubuntuforums.org/showpost.php?p=11929215&postcount=17](http://ubuntuforums.org/showpost.php?p=11929215&postcount=17)
[http://askubuntu.com/questions/66843/how-to-change-mouse-cursor-and-theme](http://askubuntu.com/questions/66843/how-to-change-mouse-cursor-and-theme)
[http://www.youtube.com/watch?v=Yxfa2fXJ1Wc&feature=g-user-u](http://www.youtube.com/watch?v=Yxfa2fXJ1Wc&feature=g-user-u)
[http://www.youtube.com/watch?v=2hu9JrdSXB8&feature=relmfu](http://www.youtube.com/watch?v=2hu9JrdSXB8&feature=relmfu)

---

### Post by pqwoerituytrueiwoq on 2012-10-06
still not working
[[IMG]http://i.imgur.com/42z7il.png[/IMG]](http://i.imgur.com/42z7i.png)

---

### Post by cariboo on 2012-10-31
A bump for the move.

---

### Post by pqwoerituytrueiwoq on 2013-01-04
I believe this is everywhere i have set the mouse and it still does not work right
it is still the original size on the desktop, window decorations, and panels
it only effects the default cursor icon (the arrow one) the other like the one shaped like a hand are fine
```
mom@desktop:~$ cat /usr/share/icons/DMZ-White/cursor.theme
[Icon Theme]
Inherits=DMZ-White
Size=48
mom@desktop:~$ cat ~/.Xdefaults
Xcursor.theme: DMZ-White
Xcursor.size: 48
mom@desktop:~$ cat ~/.gtkrc-2.0
gtk-cursor-theme-name="DMZ-White"
gtk-cursor-theme-size=48
mom@desktop:~$ cat .config/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml | grep CursorThemeSize
    <property name="CursorThemeSize" type="int" value="48"/>
mom@desktop:~$ 

```

---

