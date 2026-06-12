---
title: "looking for a couple apps..."
date: 2006-04-08
forum: General Help
---

### Post by gecl on 2006-04-08
kinda new to linux and wondering how I can set up a couple things.

1) In looking at screencaps of other people's desktop, I notice a taskbar with large icons (almost mac style at the bottom of their screen) - just wondering how i set this up...

2) I notice some people have a tab on the side of their screen that shows information such as CPU usage, processes, weather, etc. What program is this?

any help would be appreciated. Thanks

---

### Post by taurus on 2006-04-08
Those are eye candies that you can install on your Ubuntu.  Most people, including myself, use gdesklets.  You can install it with apt-get and gdesklets-data.  Then, head over to [http://gdesklets.gnomedesktop.org/categories.php](http://gdesklets.gnomedesktop.org/categories.php) and download whatever displays and sensors you want.  It has a lot of nice desklets for you to choose from.  ;)

---

### Post by John.Michael.Kane on 2006-04-08
[http://www.ubuntuforums.org/showthread.php?t=77694&highlight=eyecandy](http://www.ubuntuforums.org/showthread.php?t=77694&highlight=eyecandy)
[http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/)
[http://conky.sourceforge.net/](http://conky.sourceforge.net/)   howto listed-->                            [http://ubuntuforums.org/showthread.php?t=139262&highlight=conky](http://ubuntuforums.org/showthread.php?t=139262&highlight=conky)

---

### Post by testube_babies on 2006-04-08
"Taskbars" with large icons are just gnome-panels configured to your liking.  For instance, right-click on your top panel and you can configure it by choosing "Properties" or "Add to Panel..."

The system monitor tabs are from a program called gdesklets.  Do this in a terminal:

sudo apt-get install gdesklets gdesklets-data

And then you should be able to start up gdesklets from your Applications->Accessories menu.

---

