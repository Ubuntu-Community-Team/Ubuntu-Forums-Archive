---
title: "Desktop Enviroment vs Window Manager: Are they the same thing?"
date: 2009-10-23
forum: General Help
---

### Post by UranUtan on 2009-10-23
Hi,

I have an old P3, 1GHz with Ubuntu 9.04. I find it is rather sluggish and I am looking to how to speed it up. Reading articles and blog posts about Linux for older computers, I see that two definitions come often "**Desktop Environment**" (DE) and "**Window Manager**" (WM).

Are they two different wordings to say the same thing or are they two different things? Can you please help to clarify by answering the below questions?

Q1. In a standard Ubuntu, what is DE and what is WM?

Q2. Are DE and WM co-dependant? For example, is it possible to use Linux with only the DE or only the WM?

Q3. Same as Q1, with Windows as an example. Is the "Desktop Environment" the Windows background with a few icons and the taskbar? And is "Window Manager" Windows Explorer? (the file manager that looks like Nautilus).

Thanks in advance for any clarification.


ADDENDUM: I have read Wikipedia about the generic definitions of
([Desktop Environment]("http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments") and [Window Manager]("http://en.wikipedia.org/wiki/Window_manager")) But it is still confusing as there are system like Openbox which has a graphical interface, a WM but no DE.

---

### Post by blur xc on 2009-10-23
> **UranUtan said:**
> Hi,

I have an old P3, 1GHz with Ubuntu 9.04. I find it is rather sluggish and I am looking to how to speed it up. Reading articles and blog posts about Linux for older computers, I see that two definitions come often "**Desktop Environment**" (DE) and "**Window Manager**" (WM).

Are they two different wordings to say the same thing or are they two different things? Can you please help to clarify by answering the below questions?

Q1. In a standard Ubuntu, what is DE and what is WM?

Q2. Are DE and WM co-dependant? For example, is it possible to use Linux with only the DE or only the WM?

Q3. Same as Q1, with Windows as an example. Is the "Desktop Environment" the Windows background with a few icons and the taskbar? And is "Window Manager" Windows Explorer? (the file manager that looks like Nautilus).

Thanks in advance for any clarification.


this has been a real confusing subject for me too, there seems to be a bit of overlap between the two.  

Gnome is a DE.  So is KDE, XFCE, etc...  Compiz is a window manager, and also I think Metacity, to name two.

Now, Openbox - I don't kow what that is.  I think it runs by itself in Crunchbang Linux, but you can run it in Gnome too?  Also, I've read posts of people using Compiz by itslef w/o a DE.  Then there are window decorators?  Emerald, GTK?  

There should be an idiots guide to all of this in a sticky somewhere...

BM

---

### Post by M4rotku on 2009-10-23
This is what I read to understand it.

[http://www.ghacks.net/2008/12/09/get-to-know-linux-desktop-environment-vs-window-manager/]("http://www.ghacks.net/2008/12/09/get-to-know-linux-desktop-environment-vs-window-manager/")

All I did was google "windows manager vs desktop environment.

I hope it makes sense, it's a bit complicated, but not too hard.  They do overlap.

---

### Post by philinux on 2009-10-23
[http://en.wikipedia.org/wiki/Desktop_environment](http://en.wikipedia.org/wiki/Desktop_environment)

There is also a good link to window managers..

---

### Post by DeMus on 2009-10-23
> **UranUtan said:**
> Hi,

I have an old P3, 1GHz with Ubuntu 9.04. I find it is rather sluggish and I am looking to how to speed it up. Reading articles and blog posts about Linux for older computers, I see that two definitions come often "**Desktop Environment**" (DE) and "**Window Manager**" (WM).

Are they two different wordings to say the same thing or are they two different things? Can you please help to clarify by answering the below questions?

Q1. In a standard Ubuntu, what is DE and what is WM?

Q2. Are DE and WM co-dependant? For example, is it possible to use Linux with only the DE or only the WM?

Q3. Same as Q1, with Windows as an example. Is the "Desktop Environment" the Windows background with a few icons and the taskbar? And is "Window Manager" Windows Explorer? (the file manager that looks like Nautilus).

Thanks in advance for any clarification.

I hope I can answer these questions for you. If not I am sure somebody will shoot me immediately when reading my answers.

1. DE is Desktop Environment. It is the complete set of programs used. Your DE can be Gnome, KDE, XFCE, LXDE. Each has a complete set of programs to do this and that. Each has a certain way they look.
WM is Window manager. This is a program which takes care of the windows in the graphical user interface. Without it, your opened programs wouldn't have a window around it with the normal buttons to minimize, maximize and close the program.

2. You always need a WM, even without a DE. When you only use the command line interface (CLI) to do your stuff, you will open a grapgical program now and then. This program needs a WM to set the window straight.

3. See 1. No, a window manager is not a kind of explorer (in Windows) or better nautilus (in Gnome). It's as I wrote in 1. a program to straighten the windows so you can use the program, move the window around, maximize it, close it, etc.

If I am totally wrong guys, please shoot me. But before doing so, explain it to me please.

---

### Post by martrn on 2009-10-23
> Q1. In a standard Ubuntu, what is DE and what is WM?

A DE is a desktop enviroment, that is a complete desktop environment, includeing all programs that this would need to allow a computer user to make full use of a computer   A WM is a window manager which is a binary program used usually by a desktop environment in order to keep a list of programs that have registered the use of a window and needs displaying in someway, to the X11 server.

> Q2. Are DE and WM co-dependant? For example, is it possible to use Linux with only the DE or only the WM?
EVERY single desktop environment will have a windows manager, or it will not be able to manage its windows.  A desktop enviroment also incudes other things such as a desktop manager (for logon) a taskbar a awn manager plus more.....

> Q3. Same as Q1, with Windows as an example. Is the "Desktop Environment" the Windows background with a few icons and the taskbar? And is "Window Manager" Windows Explorer? (the file manager that looks like Nautilus).
In newer incarerations of windows the Desktop Enviroment is called "Windows Vista" or "Windows 7" and the Windows Manager for Windowze is caled DWM or DCE (Desktop Window Manager, or Desktop Compositing Engine) depending on which version of windowze you are running.

---

### Post by UranUtan on 2009-10-23
So in other words, Desktop Environment + Window Manager are the components that make up the Graphical User Interface (GUI) which allows the user to interact with the OS like moving the mouse, displaying icons, background, menus, etc. Allowing navigation within menus or file system, launching programs, managing the visual behavior of windows.

As such, I recognize Gnome or simply Windows. Then why are there distros that have only a Window Manager (CrunchBang which only has Openbox as WM)? How can we use a computer with no desktop? (no menu, no icons, no navigation, etc.). This is a new notion to me that a Window Manager could be separated from the Desktop Env. Fortunately when I started learning Ubuntu, the Window Manager was magically already installed. Until now I don't even know what WM I am using, I always thought that it was Gnome which handles the GUI.

---

### Post by P4man on 2009-10-23
> **UranUtan said:**
> So in other words, Desktop Environment + Window Manager are the components that make up the Graphical User Interface (GUI) which allows the user to interact with the OS like moving the mouse, displaying icons, background, menus, etc. Allowing navigation within menus or file system, launching programs, managing the visual behavior of windows.

As such, I recognize Gnome or simply Windows. Then why are there distros that have only a Window Manager (CrunchBang which only has Openbox as WM)? How can we use a computer with no desktop? (no menu, no icons, no navigation, etc.). This is a new notion to me that a Window Manager could be separated from the Desktop Env. Fortunately when I started learning Ubuntu, the Window Manager was magically already installed. Until now I don't even know what WM I am using, I always thought that it was Gnome which handles the GUI.

A desktop environment is a rather vague term for a set of applications. Crunchbang afaik has programs to navigate menu's, browse folders, make screenshots, has a taskbar and a system to launch apps from a menu. Its very minimalistic, but  combined I guess you could call that a "DE' its just not the entire gnome of xfce suite. Desktop is this context means more "the end user's GUI experience" than the wallpaper or its icons.

A window manager is much more clearly defined, cf the [wiki's ]("http://en.wikipedia.org/wiki/Window_manager")already posted I think.

Now I could make things harder again by mentioning window decorators (like metacity) and windowing systems (like X) :)

Anyway wikipedia does a decent job explaining. Ill just note that this hierarchy is not exclusive to linux. You have the same thing in most OSs, also in MS Windows, it also has desktop environment, a window manager, windowing system and window decorator. Its just because there is basically only 1 of each that you dont really notice. Until you install a different one like WindowsBlind.

---

### Post by OpenGuard on 2009-10-23
Just test-drive wmii or dwm and you'll get the general idea about what a WM is.

---

