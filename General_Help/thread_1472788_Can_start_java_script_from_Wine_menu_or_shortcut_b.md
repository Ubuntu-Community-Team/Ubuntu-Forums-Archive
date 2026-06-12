---
title: "Can start java script from Wine menu or shortcut but not from command line"
date: 2010-05-04
forum: General Help
---

### Post by GH68 on 2010-05-04
In my Wine menu I can start an application called "Datakokboken" and I also added a shortcut to the desktop (from the Wine menu). Double clicking the icon on the desktop also starts the application without any problem. When I look at the properties of the desktop shortcut it says that the command is: ```
env WINEPREFIX="/home/gunnar/.wine" wine "C:\Program Files\Allt om Mat\Datakokboken\jre1.6\bin\javaw.exe" -classpath cookbook.jar se.bonnier.bt.cookbook.CookBookMainGui
```
Now I thought I should be able to type in the same command from the command line, but I then get a "Java Virtual Machine Launcher" dialog box saying "Could not find the main class. Program will exit". In the command window I see the following messages:
```
Exception in thread "main" java.lang.NoClassDefFoundError: se/bonnier/bt/cookbook/CookBookMainGui
Caused by: java.lang.ClassNotFoundException: se.bonnier.bt.cookbook.CookBookMainGui
	at java.net.URLClassLoader$1.run(Unknown Source)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at sun.misc.Launcher$AppClassLoader.loadClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at java.lang.ClassLoader.loadClassInternal(Unknown Source)

```

Does anyone have a clue of what I should type into the command window to start the application?

Thanks

---

