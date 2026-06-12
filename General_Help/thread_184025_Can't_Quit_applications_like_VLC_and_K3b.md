---
title: "Can't Quit applications like VLC and K3b"
date: 2006-05-29
forum: General Help
---

### Post by vinodis on 2006-05-29
It does not happen very often but if it happens you cant close them at any cost. Does anyone have a clue on how to KILL those programs?(not from the cmd line)
The VLC one is especially problematic as the close button would close the application window, but still playing the Video somwhere in background.

Alltogether, It feels shaky when using such multimedia apps.

---

### Post by Jucato on 2006-05-29
That's a weird behavior indeed. What version of KDE are you using?
Anyway, if you need to shutdown programs from the GUI (graphically), there are two ways:

1. Ctrl+Alt+Esc: this will turn your cursor into a skull shape. Anything you left-click with this will shutdown. To disable this without shutting anything down, just right-click anywhere. (an equivalent of this keyboard combo is typing "xkill" in the Run Command box).

2. Ctrl+Esc: this brings up the KSysGuard, somewhat an equivalent of Windows' Task Manager. You will see here the list of running programs. You can search for a program by typing its name on the search bar near the top of the window. To end a process/app, click on it and press Kill at the bottom. It will ask you for confirmation.

Now don't get too trigger happy and start killing things. :D

---

### Post by vinodis on 2006-05-29
Thanks very much to those tips. I am using the KDE which came along with the Breezy.

---

### Post by Jucato on 2006-05-29
I see, so you are using KDE 3.4.3. The latest version available is KDE 3.5.3
You'll have that once you're able to upgrade to Dapper (which is what I think you're trying to do, based on your posts in KubuntuForums.Net?)

---

### Post by vinodis on 2006-05-30
Yes!. Tried editing the sources.list to get to dapper without succes. Hopefully i will get some inputs today from here. :)

---

### Post by moopere on 2006-06-04
[QUOTE=vinodis]It does not happen very often but if it happens you cant close them at any cost. Does anyone have a clue on how to KILL those programs?(not from the cmd line)
The VLC one is especially problematic as the close button would close the application window, but still playing the Video somwhere in background.

Alltogether, It feels shaky when using such multimedia apps.[/QUOTE]

Yes, VLC is doing this weird 'background play' thing to me too.  I'm on Dapper using KDE 3.5.3 (from kububu.org).

Craig

---

