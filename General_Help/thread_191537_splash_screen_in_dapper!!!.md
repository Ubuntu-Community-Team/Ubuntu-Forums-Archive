---
title: "splash screen in dapper!!!"
date: 2006-06-07
forum: General Help
---

### Post by kickstar on 2006-06-07
sorry for this dumb question but how do you change the splash screen in dapper?

Thanx

---

### Post by xXx 0wn3d xXx on 2006-06-07
You can change it through [ this wiki tutorial. ](https://wiki.ubuntu.com/USplashCustomizationHowto?highlight=%28custom%29%7C%28usplash%29) You can also use [ this thread ](http://ubuntuforums.org/showthread.php?t=82835&highlight=usplash) or this very nice [ Serengeti Usplash for Dapper. ](http://ubuntuforums.org/showthread.php?t=185540&highlight=usplash)

---

### Post by johnc4510 on 2006-06-07
You could also do this:
Your splash images are in:/usr/share/pixmaps/splash
Go to:Applications>Sysetm Tools>Configuration Editor
Click on apps, Click on gnome-sessions, Click on Options
Before you do anything else, Bookmark the page by clicking on Bookmark and add
Where you see:splash_image, right click on that and choose Edit Key
You can then change the image to one in the spash file. NOTE: Leave the first part (splash/) and only change the image name.Click OK and the splash will be changed.
Note: To put new splash images in the /usr/share/pixmaps/splash folder do this:
sudo nautilus
navigate to the above named file. Then drag and drop the image into it and close the window and exit the terminal.

---

### Post by nismoskys on 2006-06-07
are you looking for usplash or the gnome splash screen?
for the gnome splash just ```
sudo apt-get install gnome-splashscreen-manager
```
just place your downloaded splash screens in ~/.splash (make it if not already there) and load them from the splashscreen manager.

---

### Post by xXx 0wn3d xXx on 2006-06-07
[QUOTE=nismoskys]are you looking for usplash or the gnome splash screen?
for the gnome splash just ```
sudo apt-get install gnome-splashscreen-manager
```
just place your downloaded splash screens in ~/.splash (make it if not already there) and load them from the splashscreen manager.[/QUOTE]
Wait...My fault I thought he was talking about Usplash...sorry for my stupidity.

---

