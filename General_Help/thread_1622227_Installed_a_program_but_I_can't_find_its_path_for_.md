---
title: "Installed a program but I can't find its path for startup manager"
date: 2010-11-15
forum: General Help
---

### Post by Sxynerd on 2010-11-15
I installed a new program called the "Android Notifier Desktop 0.2.1" and within the program it say to use the systems startup manager to start the program with every system boot.

I have no idea where to begin looking for the programs file and main start up link.


Please help.

[IMG]http://i44.photobucket.com/albums/f33/wolvee123/Androidscreeenshot.png[/IMG]

---

### Post by CharlesA on 2010-11-15
The docs say that it'll be found in the applications menu once it's installed.

[http://code.google.com/p/android-notifier/wiki/LinuxInstalation](http://code.google.com/p/android-notifier/wiki/LinuxInstalation)

---

### Post by pqwoerituytrueiwoq on 2010-11-15
go to main menu editor (system->preferences) find the app you want click edit and copy the command it uses

---

### Post by Sxynerd on 2010-11-15
I must have miscommunicated what I am trying to do because neither of the suggestions made sense.

I know how to start the program.  In fact if you look at the picture, it is started and you can see that I am trying to find the program path for Ubuntu's "startup manager".

[LIST]
[*]I want the program to start on it's own every time the PC boots.

[*]This is not achievable using the programs internal settings.  ..the program directs me to use the "Startup manager"

[*]When I go to startup manager, I am given the full directory to choose from.  I do not know where to go to select the proper path to the program.
[/LIST]

.i.e c:\ Simon\ Garfunkel.exe

---

### Post by dino99 on 2010-11-15
search "android" under nautilus, then check the package properties by right clicking, there you will find its path

---

### Post by stinkeye on 2010-11-15
> **Sxynerd said:**
> I must have miscommunicated what I am trying to do because neither of the suggestions made sense.

I know how to start the program.  In fact if you look at the picture, it is started and you can see that I am trying to find the program path for Ubuntu's "startup manager".



If you know how to start it just right click on the icon in the notification
area and choose **start at login** in preferences.


They weren't telling you how to open the program, but how to find out the start command.
eg alt+F2 and run **alacarte** (the main menu editor).
Then go to accessories and you'll see **Android Notifier Desktop**.
Double click on it and it will show you the start command.
```
/usr/share/android-notifier-desktop/run.sh
```

---

### Post by Sxynerd on 2010-11-15
> **stinkeye said:**
> If you know how to start it just right click on the icon in the notification
area and choose **start at login** in preferences.


They weren't telling you how to open the program, but how to find out the start command.
eg alt+F2 and run **alacarte** (the main menu editor).
Then go to accessories and you'll see **Android Notifier Desktop**.
Double click on it and it will show you the start command.
```
/usr/share/android-notifier-desktop/run.sh
```

OK, that makes a bit more sense.  I was trying to right click in the "Applications/accessories/android" menus expecting something to happen and nothing did. (Except add to launcher panel etc)

The way you just explained it in your edit made sense and I was able to see the info I would have needed.

The way I figured it out was by adding a desktop icon, R clicking properties, copying the source, filling it into the "startup manager" and then deleting the icon. 

Thanks for you help everyone.  I know it can be frustrating working with/helping Noobs out.

---

### Post by stinkeye on 2010-11-15
Good to see you got it sorted.
P.S Just choosing start at login in **Android Notifier Desktop** preferences works for me.

---

### Post by uriel1998 on 2010-11-21
As an alternative, you could also copy the launcher to

```
/home/USER/.config/autostart
```

Or if you want even more control, put a script there that calls everything else you want.

---

### Post by E@zyVG on 2011-02-19
Downloaded the latest x64 version from the site. When I run it I get "Could not load UI. Make sure you are using the correct version ...."

```


vg@subnote-nix:~$ /usr/share/android-notifier-desktop/run.sh 
2011-02-19 16:50:15,443 INFO [ApplicationImpl] - Starting SWT
2011-02-19 16:50:15,557 ERROR [ApplicationImpl] - Error starting SWT
java.lang.UnsatisfiedLinkError: Cannot load 64-bit SWT libraries on 32-bit JVM
	at org.eclipse.swt.internal.Library.loadLibrary(Unknown Source)
	at org.eclipse.swt.internal.Library.loadLibrary(Unknown Source)
	at org.eclipse.swt.internal.C.<clinit>(Unknown Source)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Unknown Source)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Unknown Source)
	at org.eclipse.swt.widgets.Display.<clinit>(Unknown Source)
	at com.notifier.desktop.app.SwtManagerImpl.start(SwtManagerImpl.java:44)
	at com.notifier.desktop.app.ApplicationImpl.start(ApplicationImpl.java:69)
	at com.notifier.desktop.Main.main(Main.java:106)

```

Have both 32 and 64 bit Java installed.

---

