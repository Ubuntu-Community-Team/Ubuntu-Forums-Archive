---
title: "Kubuntu kde 4.3 how to get back default panel"
date: 2010-01-04
forum: General Help
---

### Post by hatewindows7 on 2010-01-04
I messed up with panel on kde 4.3 I lost wifi knetwork manager and some other stuff I want to reset to factory default kde 4.3 panel 
I googled it but found solutions for kde3.5 which are not working with kde 4.3
please let me know how can I get back panel
new user help

---

### Post by Marrkk on 2010-01-04
right-click on desktop .. add panel ?

if you dont get this option, you may have to set your desktop settings as 
'desktop' or 'folder; when u right click on the desktop..
hth
Mark







[http://marrcuk.blogspot.com/]("http://marrcuk.blogspot.com/")

---

### Post by hatewindows7 on 2010-01-04
Thanks mark......but if I do it is adding an empty panel .... My requirement is to get all icons on the default panel which I got when first installed kde I need to reset to factory default kde panel which is very useful one please help me

---

### Post by Marrkk on 2010-01-04
yes.. so.. add the panel..
you can customise this list of course, but here's whats on mine ..
add these in order.. so right click on the panel - tpanel options / add widgets ok ?   cool.

first up, the menu button, so in the widget list add these ..
Application launcher
Task manager
pager
device notifier
system tray
battery monitor  (well on my panel anyway!)
digital clock
 .. is that anything like ?
hth
mark

---

### Post by Marrkk on 2010-01-04
if that works for you, uremember u can 'lock' the panel .. and widgets :)

---

### Post by hatewindows7 on 2010-01-04
I alredy did that but I am missing a tray icon for wifi connecions that's is part of knetworkmanager when I add it to the panel the icon is nt working so I am missing some more useful widgets that comes default with kde so is there any one who did with kde 4.3 I do not want to total reinstall kde for the sake of this if kde supports any factory back system like windows restore point please let me know

---

### Post by hatewindows7 on 2010-01-04
does any one know how to get back my default panel back with all widgets in kde latest version please

---

### Post by Chris Musampa on 2010-01-04
Not sure but you could try renaming your .kde folder:
Log out of kde, press crtl+alt+f3, log in to the terminal with your usual name and password then type:
```
mv ~/.kde ~/.kde-old
```

then press ctrl+alt+f7, log in to kde again and hopefully the desktop resets itself.  Not sure if it'll work but if your next option is reinstalling kde then it's probably worth a go first.

---

