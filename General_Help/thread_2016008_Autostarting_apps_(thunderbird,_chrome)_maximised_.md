---
title: "Autostarting apps (thunderbird, chrome) maximised and in workspace x"
date: 2012-07-04
forum: General Help
---

### Post by ubnewbie2 on 2012-07-04
Is there a way to autostart applications like thunderbird and Google chrome browser, in a particular workspace and maximised? I'd like to start each one in a different workspace of my choosing.

---

### Post by msammels on 2012-07-04
[This](https://help.ubuntu.com/community/AddingProgramToSessionStartup) should help for running programs at startup... not sure about separating them though, will look around and see what I can dig up.

---

### Post by ubnewbie2 on 2012-07-04
> **msammels said:**
> [This](https://help.ubuntu.com/community/AddingProgramToSessionStartup) should help for running programs at startup... not sure about separating them though, will look around and see what I can dig up.

Thanks.

Actually those instructions seem a bit out of date compared to what I see in 12.04, but I found a way to set startup applications.  There's a menu item for it under the on/off shutdown/suspend panel icon.

At the bottom of the linked page however, is a reference for a way to use a thing called Devil's Pie to move apps to workspaces, but it seems VERY complicated.

---

### Post by pt123 on 2012-07-07
use wmctrl to move to a particular workspace and then start the application

or use compiz to set windows to a particular workspace

---

### Post by ubnewbie2 on 2012-07-07
> **pt123 said:**
> use wmctrl to move to a particular workspace and then start the application

or use compiz to set windows to a particular workspace

It would seem that wmctrl manages desktops, and that workspaces are a subdivision of each desktop.  So I can move an app to the second desktop, but then it can't be seen anymore in any workspace (as shown by workspace switcher) until I use wmctrl to switch desktops, then workspace switcher shows 4 new workspaces with just the one moved app in one of them.

About compiz though...  I am not sure what you mean.  How do I use that?

---

### Post by pt123 on 2012-07-07
you can switch to viewports
```

wmctrl -o 4000,1500  

```
where 4000 pixels along the x and y is 1500 pixels
so on on a 1680x1080 wide screen this will be in the 3rd column 2nd row workspace

Compiz in CCSM Window Management - > Place Windows

---

### Post by ubnewbie2 on 2012-07-07
> **pt123 said:**
> you can switch to viewports
```

wmctrl -o 4000,1500  

```
where 4000 pixels along the x and y is 1500 pixels
so on on a 1680x1080 wide screen this will be in the 3rd column 2nd row workspace

Compiz in CCSM Window Management - > Place Windows

Got it working with Compiz CCSM.  Thanks heaps.

---

### Post by BoogeyOfTheMan on 2012-07-07
I'm interested in something similar, I want certain apps to start on certain workspaces, but I dont want them maximized. I'd also like to have them positioned so as not to cover my conky.

Where in Compiz CCSM would one accomplish something like this on 11.04?

---

### Post by pt123 on 2012-07-07
probably the same place

---

### Post by ubnewbie2 on 2012-07-07
Yep there are three ways to control Windows, fixed positions, placement mode, and fixed viewport, and you can use them in combo.  You would use the first and last I think.

---

### Post by BoogeyOfTheMan on 2012-07-07
It doesnt seem to be working for me (probably not doing it right). Whenever I start the app, it still starts on the active workspace in whatever position it feels like.

Anyone know where I can find explainations for what some of those options under fixed window placement do?

---

