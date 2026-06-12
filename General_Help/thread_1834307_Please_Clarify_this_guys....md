---
title: "Please Clarify this guys..."
date: 2011-08-27
forum: General Help
---

### Post by Deviant06 on 2011-08-27
Hey guys, got a new pc, and I'm back on ubuntu 11.04
I upgraded to Gnome 3.02 and I have the normal unity "style" left bar (single vertical row) 
But I've been looking online, and I keep seeing something like [http://tekzen.files.wordpress.com/2010/05/workspace.png](http://tekzen.files.wordpress.com/2010/05/workspace.png)

Is there anyway I can get that type of panel in my gnome 3?

I'm still a bit unsure about the difference between Gnome 3 and Gnome Shell.



Can anyone point me in the right direction?

---

### Post by sanderd17 on 2011-08-27
Gnome3 is the bases (window management ...), Gnome-Shell is the visible interface.

Unity needs gnome (2 or 3) as a base too, but Unity does not need gnome-shell.

A gnome3 theme (also called GTK+ theme) is responsible for rendering the buttons inside windows, rendering the window borders ... while a gnome-shell theme is responsible for the activities bar, the overview menu ...

As for that interface, that's the interface of one of the beta releases of Gnome-Shell. I don't know if there is code around that makes it back like that.

---

### Post by Deviant06 on 2011-08-27
so that style is no longer available? I would have to find a beta version and downgrade to that? =/ 
Or is that one of the current betas of Gnome 3?  I really like how it's setup. 
Its much easier to get to what you use most often, and have more area for buttons, which I like. 
If anyone knows how to get it.. I would appreciate it..
[http://tekzen.files.wordpress.com/2010/05/workspace.png](http://tekzen.files.wordpress.com/2010/05/workspace.png)


(Left side bar)

---

### Post by dino99 on 2011-08-27
[https://wiki.ubuntu.com/Unity](https://wiki.ubuntu.com/Unity)

---

### Post by sanderd17 on 2011-08-27
> **Deviant06 said:**
> so that style is no longer available? I would have to find a beta version and downgrade to that? =/

Those betas were unstable (crashing every 10 minutes). So I wouldn't downgrade. And that "Recent files" utility didn't work too good for me. When I was working on a LaTeX document for example, than all output files were in that view, including log files. Or if I imported photo's, than all I could see was a list of files that started with "2011-05-03..." (and the rest was unreadable). So I can understand why they got rid of it.

I also got problems with app icons. Some apps had bigger icons than others. And if there was one app with a big icon in your "recent apps" list, it messed the whole layout. This probably could be fixed, but they didn't fix it.

Workspace management is also a lot more intuitive now. You know which workspace is the first, which the second ... so that you can switch with hotkeys. When the workspaces were arranged like in the betas, they were numbered as follows:

```

 1  2  5 10
 3  4  6 11
 7  8  9 12
13 14 15 16

```

So it was very difficult to arrange your windows in a way that it looks good from the overview window and that you still can use hotkeys.

That old interface may look good, but it wasn't very good.

---

### Post by sanderd17 on 2011-08-27
Btw, my workflow in GS is as follows:

[LIST]
[*]Opening a program: Hit the super key, type the first letters (like "fir" for firefox) and hit enter
[*]changing between programs: use ALT+TAB or ALT+` (key above tab)
[*]looking if a download is progressing: Press the super key to see the window, press it again to go back
[/LIST]

And the overview window is quite intuitive with drag-and-drops. You can just drag an application (a window or an icon) to a workspace. Or you can drag an icon to the dock, or away from the dock.

---

