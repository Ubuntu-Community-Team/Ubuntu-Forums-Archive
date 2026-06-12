---
title: "Can't get KGrubEditor to start?"
date: 2009-10-16
forum: General Help
---

### Post by rob86 on 2009-10-16
I've been trying to get KGrubEditor working and it won't start. It pops up in the task bar and disappears. I'm thinking I might have to run it with gksudo but  I can't even try that, because I can't find where the executable file is. I tried every command I could think of to start it, kgrubeditor, kgrub, KGRUBEditor, and nothing works. It's in the "System" menu but it won't show me the path.

Any suggestions?

---

### Post by mechro on 2009-10-16
Synaptic will give you the list of installed files. Set synaptic preferences to "Show package properties in the main window".

---

### Post by mechro on 2009-10-16
Hmmm... I see what you mean. I installed it and I figured out the command is **gksudo kcmshell4 kgrubeditor**. It starts up slowly and there's a hell of a lot messages thrown up in the Terminal so I guess it's one of those KDE apps that doesn't run well in Gnome.


Edit: I've run it a second time and it's now OK. Perhaps it has to configure itself first time round. It's actually quite cool. I think I'll keep it.:D

---

### Post by rob86 on 2009-10-16
That command works, I don't know how you figured to put kcmshell4 in there but anyway. 

I see all the output in the terminal  but you're right it goes away after the first start. I haven't used KGrubEditor before,  I just saw it on a webpage and thought I'd try it out.

---

### Post by mechro on 2009-10-17
> **rob86 said:**
> That command works, I don't know how you figured to put kcmshell4 in there but anyway. 


When I installed it, it appeared in Applications > System Tools. To find the command for menu items, right-click the menu bar > Edit menus, find the application, right-click it and it gives you Properties which includes the relevant command.

---

### Post by rob86 on 2009-10-17
That was one of the first things I tried when attempting to identify the path, but it didn't work. It must be because I'm using Xfce instead of GNOME. 

For future reference, where is the path to the "Start Menu" ? Like on Windows, there'd be a folder Start Menu\ full of links. Does Ubuntu have something like this, or does it work differently? I noticed that Gnome and Xfce had slightly different App menu's in regards to how they were organized.

---

### Post by mechro on 2009-10-17
I'm not exactly sure how Gnome builds a menu but if you navigate to usr/share/applications all your "desktop" applications should be in there. If it's a KDE app you'll also find some KDE folders in there.

If you're using Thunar in xfce the Properties > Launcher tab item should give you the application's command.

---

### Post by juky on 2009-10-25
Remove kgrubeditor, install QGrubeditor, voila!

[http://packages.ubuntu.com/hardy/admin/qgrubeditor](http://packages.ubuntu.com/hardy/admin/qgrubeditor)

Cheers,
juky

---

### Post by Sun.Dial on 2009-10-25
Hi, I'm new to all this so may have taken a shortcut to far, but following what Mechro said earlier about right clicking to find the command, I typed gksudo in front of it in the box, and then it worked by clicking from the Apps menu... is that allowable?

---

