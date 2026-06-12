---
title: "Some Terminology Help"
date: 2010-04-16
forum: General Help
---

### Post by th5th on 2010-04-16
Ok so this isn't really a support issue, but I would appreciate some help. I am going to be getting a netbook pretty soon (I was on here last week asking fro recommendations) and I would like to build my own lightweight system from the ground up.

I know there is lots of information about how to do this, and what applications are good for this sort of thing, so **I am not asking about that!**

What I would like help with is a few definitions / terms that I am not 100% clear on:


[LIST]
[*]**X-org / X server.** This confuses me. Wikipedia suggests it has a lot to do with network connections, but I have only ever seen it discussed in a display context? It provides some sort of framework on which a GUI can run, right?
[*]**Window Manager. **I know some examples, but what is one of these?! I mean really. Does it simply define styles and behaviour of windows which are created by X?
[*]**File Manager.** I have a sort of vague idea about this. But what would differences be between file managers? Does it just determine how files are presented within windows, and what you can do to them?
[*]**Desktop Environment.** I think this is just an umbrella term for everything all together? So GNOME is Metacity + Nautilus + other stuff.
[/LIST]
So my plan is to install a minimal Lucid Lynx comman line install, and then add, for example, fluxbox, pcmanfm, wicd and a few other bits and pieces. Do I need anything else to make a really lightweight desktop? (I don't mean applications, I mean fairly low level "make-your-computer-into-something-you-can-interact-with-like-it's-2010").

Help appreciated. Sorry if this should be posted elsewhere...

EDIT: Ok so I found [this ]("https://help.ubuntu.com/community/Openbox")which explained WMs and DEs, and also got me interested in Openbox...

---

### Post by jbrown96 on 2010-04-16
The X-server is a "network" server that sends display information. It draws all your windows, menus, panels, etc. Unix operating systems, which includes Linux, use a data transfer mechanism called pipes and sockets. If you run a program from the terminal, the output you see is sent through a pipe and is displayed on screen. The program will "write" data to a pipe and the terminal is connected to it and "reads" the data from it. This is how programs share information between them. Sockets are basically the same thing, but can work between machines. The important thing is "can." The gets information over sockets and then sends its output on another socket. This can go to another computer, or more likely, gets sent to your video card and then displayed on screen. A lot of people think this causes a performance penalty, but it doesn't; however, it does make the X server really powerful. 
The X server can do all sorts of things, but we typically only need it to do some very basic operations. I hate to use a car analogy, but a car is like the X server. It has tons of sub-systems (breaking, transmission, engine, etc.) all of which are very complex. There is no way a driver could manage all of those himself. That's why we let the car take car of most of that, and the driver is only concerned with steering, breaking, and acceleration. That's really what the window manager is. It allows programmers to easily create applications without having to deal with all of the complexity of the X server. Just drawing a window frame is very complicated using X, but if you can use something like QT (for KDE) or GTK+ (for Gnome), it's one or two lines in a program versus hundreds in X. Furthermore, there's other benefits like applications look consistent, which is good for users. There are also lots of built-in features. When you save a file in an application, the save file dialog looks consistent across programs; programmers can use a template and create programs faster. Window managers simplify programming and give consistent, easy-to-use features. 
A file manager is just a graphical representation of your files. You can click on folders to open them or open files. There are additional features built-in to file managers. Dolphin (KDE)and Nautilus (Gnome) both have features to connect to file servers. There's copy/paste functionality. There are fairly straight forward. If you use something like Fluxbox, then its file manager is going to be one of the most obvious differences. It will lack a lot of features. 
Desktop environment is really just a collection of "libraries." They have their own window manager, typically toolkit (see below), and applications. These are installed with kubutu-desktop or ubuntu-desktop lubuntu-desktop, etc. They are usually very large. 

Toolkits are really the underlying reason for all of this discussion. X has a toolkit. Gnome has a toolkit: GTK+, and KDE has QT. These are a set of libraries that developers can use to more easily create applications. When you login to a Gnome desktop then many GTK+ libraries are loaded into memory. When you launch a Gnome app, you may need to load more GTK+ libraries. The problem comes in when you start mixing applications. If you have a Gnome desktop and run QT applications, then you will have GTK+ and QT libraries loaded into memory. This uses more of your memory. That's why it's recommended that you use applications that match your Desktop Environment. That's why I generally discourage people from using Fluxbox and other lightweight DEs. Since you will probably be running GTK+ or QT apps, then you're not really saving any memory. Stick with the one that matches your apps.

---

### Post by th5th on 2010-04-17
Thanks jbrown! Excellent informative post. That's given me some food for thought...

> **jbrown96 said:**
> That's why I generally discourage people from using Fluxbox and other lightweight DEs. Since you will probably be running GTK+ or QT apps, then you're not really saving any memory. Stick with the one that matches your apps.

Anyone got any advice on this? It seems like I *can* get a fast, low memory system, but will have to avoid desktop-specific applications. So does anyone have any recommendations? I will be using the netbook for browsing the internet almost exclusively, with some light programming / text stuff on the side whilst away from my desktop. I was thinking:

- Lucid Lynx
- Openbox / Fluxbox etc.
- XFE or PCmanFM
- SLiM
- Google Chrome - is this GNOME / GTK based or what?
- A few other bits...

Or maybe I should stick with a gnome-core install?

Advice appreciated! Oh an if anyone has experience running Ubuntu on the new Samsung NB30s throw that in too :)

---

