---
title: "Change icons on Natty's Unity"
date: 2011-05-22
forum: General Help
---

### Post by dakukuu on 2011-05-22
How do you change the icons on the Unity dock? I used to drag and drop icons onto the toolbar and it would provide an options menu with running preference, icon, name, comment, etc. On Natty however, when i drag my icon on to the dock, it seems to provide a very low detailed image, and i can't seem to find any way to change it.

I tried finding the launcher used previously, except i can't seem to find that either. Please help, it's a complete eyesore, and i like Unity.

Here's a screen-shot of what I mean.
[IMG]http://img804.imageshack.us/img804/9257/dsktp.png[/IMG]
EDIT: Also, now i have closed the program, it has a grey icon with a ? in it.

EDIT2: Also, how you do set default programs now?

---

### Post by Sheddingmyskin on 2011-05-23
Changing your gtk theme should change some of them.

A round-about way of changing the icons would be to create a launcher on the desktop (right-click > Create Launcher)
Type: choose application
Name: friendly name
command:  command typed in terminal to open application
comment: Description of application.

You can then change the icon to whatever you want by selecting the properties of the application and clicking the icon button on the properties page.
Once icon is set, drag and drop the icon to the Unity launcher bar.

---

### Post by ragtag on 2011-05-30
Check out [this guide]("http://maketecheasier.com/8-really-useful-ubuntu-unity-quicklists/2011/05/07/") on how to customize your Unity dock.

If you place your launcher in /usr/share/applications/ it will also show up as an installed application, when browsing. You can look at some of the other .desktop files there, for what options are available.

---

