---
title: "Games without GUI"
date: 2012-06-11
forum: General Help
---

### Post by unitedanarchy on 2012-06-11
Is there any way for me to go into the command prompt like how you can when you go into the root recovery mode terminal so you have no GUI currently running and run a game like minecraft and play it? So basically the terminal screen change into minecraft just like when you run aptitude so then it will be way faster?

---

### Post by Zvlwab on 2012-06-11
put an & after the command you run. Then go to the terminal and press CTRL-D.
Though it would make more sense to just create a Minecraft Shortcut in the menu.

---

### Post by greenpeace on 2012-06-11
If I understand properly what it is that you want to do, you're still going to need a running version of a window manager to provide the graphical environment where the game can run...

...maybe there's a way to fire up a copy of X for just your games, but I think you are going to find that quite complicated to set up.

---

### Post by unitedanarchy on 2012-06-11
Hmm, Well it's just that my screen can physical display data, And that it has the ability to give it data to display. I don't see why it should be too difficult to have minecraft for example run like aptitude does.

---

### Post by cortman on 2012-06-11
Aptitude uses a display library called ncurses. Minecraft is not programmed to utilize it. Therefore, no, it will not work. You need X server running.

---

### Post by efflandt on 2012-06-11
If you are only running a minecraft "server", that can run from a terminal or console because the server itself has no graphical output.

But while the minecraft "client" can be launched from a terminal, it will not display any graphics without a gui.  Minecraft uses lwjgl [http://www.lwjgl.org/](http://www.lwjgl.org/) which does not replace system inputs and audio/video drivers, it just provides java hooks into those to make writing cross platform games easier.

---

### Post by unitedanarchy on 2012-06-12
Is there anyway to do what I want at all?

---

### Post by cortman on 2012-06-12
> **unitedanarchy said:**
> Is there anyway to do what I want at all?

Sure- download the source code and re-write it to use ncurses or some similar graphics library, although I'm not sure even how that would work as it's Java based.

---

### Post by unitedanarchy on 2012-06-12
I don't know if you can or can't see this but this isn't showing up for me for some reason. I was going to say that the source is closed which sucks, And I also wouldn't know how. But then could I just have the bare minimum running to rdisplay minecraft and nothing more?

---

