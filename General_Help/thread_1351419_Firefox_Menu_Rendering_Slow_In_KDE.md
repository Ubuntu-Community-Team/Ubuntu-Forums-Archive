---
title: "Firefox Menu Rendering Slow In KDE"
date: 2009-12-10
forum: General Help
---

### Post by velorider on 2009-12-10
When I run Firefox on KDE4 any time a menu is displayed the rendering is very slow, up to 2 seconds to display a menu.  This could be the File menu, context menu, or even a popup div.  

I've tried all the suggestions regarding removing extensions and plugins.  Still nothings helped.  However, when I run Firefox as root, kdesudo firefox.  It performs perfectly.  The only visible difference is when running as root the default firefox appearance is used.  When running as a normal user the QTCurve widget set is used. 

This leads me to believe the problem might be related to the QTCurve.  I've select other styles from the Appearance->GTK settings but still the same problem.  Is it possible to allow Firefox to use it's default appearance?

---

### Post by lovinglinux on 2009-12-10
There is a menu delay option somewhere on Firefox about:config but I can't remember which one.

Have you noticed other types of delays, not related to menus? Perhaps a database optimization could help. See the database optimization section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). I'm not sure it will help with this menu issue, but it won't hurt and will improve Firefox overall performance.

---

### Post by velorider on 2009-12-10
Thanks for the replay.  I've tried the menu setting.

The problem seems to be a general rendering problem.  I can tell by the way firefox draws itself on startup that there is something not right.  When I start with kdesudo firefox, it renders the window very quickly.  When starting as a normal user it draws very slowly.  


I believe it has something to do with the KDE GTK rendering.  When starting firefox as root the KDE GTK render stuff doesn't happen and the window pops right up.  When starting as a normal user it has the KDE feel.  

Is there a was to disable the KDE GTK integration so GTK apps render with a KDE look.

---

