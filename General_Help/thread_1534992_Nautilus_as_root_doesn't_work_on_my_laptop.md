---
title: "Nautilus as root doesn't work on my laptop"
date: 2010-07-20
forum: General Help
---

### Post by JBA2337 on 2010-07-20
Two screenshots are attached.




On my laptop (a Toshiba Satellite A105) when I open nautilus as root the window that opens is screwed up. If I type [code] "gksudo nautilus" at a terminal prompt, screenshot-1 is what I see.

[ATTACH]164038[/ATTACH]

The title bar has the word "root" instead of "root - File Browser" as it should be. There is no main toolbar, location bar, and no side bar. The next line beneath the title bar shows File, Edit, View, Places, Help instead of File, Edit, View, Go, Bookmarks, Help. If I click on View there are no checkboxes for Main Toolbar, Side Pane, Location Bar, and Status Bar. If I click on anything and then slightly move my mouse the nautilus window immediately closes. Therefore, I can't use nautilus at all to do anything. 

This strange behavior only happens when I open nautilus as root. If I open nautilus normally, there are no problems. Screenshot-2 shows the window that opens if I run nautilus as root on my desktop computer.

[ATTACH]164039[/ATTACH]

There are some things in Ubuntu that must be done using nautilus as root. I have run fsck several times, and I also uninstalled nautilus and then reinstalled it , but that didn't fix the problem.

Does anybody have an idea how to fix this problem?

JBA2337

---

### Post by WorMzy on 2010-07-20
> There are some things in Ubuntu that must be done using nautilus as root.
Really? I've managed to get by without ever needing to. :|

sudo mv|cp|rm

I've never come across a situation where those commands will not suffice.

Still, to fix this problem, run
```
gksu gconf-editor
```

Browse to "/apps/nautilus/preferences" and check "always use browser".

Voila.

---

### Post by JBA2337 on 2010-07-20
> **WorMzy said:**
> Really? I've managed to get by without ever needing to. :|

sudo mv|cp|rm

I've never come across a situation where those commands will not suffice.

Still, to fix this problem, run
```
gksu gconf-editor
```

Browse to "/apps/nautilus/preferences" and check "always use browser".

Voila.
_______________________________________________________________________

I already tried that. It makes no difference whether "always use browser" is checked or not. Nautilus when opened as root is still messed up.

JBA2337

---

### Post by mcduck on 2010-07-20
> **JBA2337 said:**
> _______________________________________________________________________

I already tried that. It makes no difference whether "always use browser" is checked or not. Nautilus when opened as root is still messed up.

JBA2337

Did you check the option in Nautilus *running as root*. Just go to Edit/Preferences, Behavior-tab and disable "Open each folder in it's own window". Because the view you see is the spatial mode of Nautilus, and the setting suggested *is* what switches between browser mode and spatial mode.

Anyway, if that doesn't solve your problem then you should simply delete (or move somewhere else until you confirm that it fixes the problem) nautilus's configuration files from root's home to reset all it's settings to defaults.

---

### Post by drs305 on 2010-07-20
You can install an app called "nautilus-gksu". It adds a right click option to open a folder as root. 

I've had problems from time to time with opening nautilus as root but the right click "Open folder as administrator" hasn't failed me yet.

---

### Post by JBA2337 on 2010-07-20
> **drs305 said:**
> You can install an app called "nautilus-gksu". It adds a right click option to open a folder as root. 

I've had problems from time to time with opening nautilus as root but the right click "Open folder as administrator" hasn't failed me yet.
________________________________________________________________________

Thanks for the suggestion, but it did not work. Nautilus-gksu is installed. I have a launcher that is set up to run [code] "gksu nautilus" in a terminal. When I right click on this launcher and select "Open folder as administrator", I get the same results. Nautilus is still messed up as described in my original post.

JBA2337

---

### Post by drs305 on 2010-07-20
As I said, I had problems running nautilus as root. Eventually they went away, although I don't know if it was an app update, kernel update, or something else. 

If all your other "sudo" functions are running correctly, you could do as I did in the interim, use "pcmanfm" or "pcmanfm2". It worked for me with "gksu pcmanfm" in a launcher even though "gksu nautilus" did not. It is *not* a solution but it is a workaround. Hopefully someone will have a real solution for you.

---

### Post by philinux on 2010-07-20
> **JBA2337 said:**
> ________________________________________________________________________

Thanks for the suggestion, but it did not work. Nautilus-gksu is installed. I have a launcher that is set up to run [code] "gksu nautilus" in a terminal. When I right click on this launcher and select "Open folder as administrator", I get the same results. Nautilus is still messed up as described in my original post.

JBA2337

what about post 4 suggestion?

---

### Post by JBA2337 on 2010-07-20
> **mcduck said:**
> Did you check the option in Nautilus *running as root*. Just go to Edit/Preferences, Behavior-tab and disable "Open each folder in it's own window". Because the view you see is the spatial mode of Nautilus, and the setting suggested *is* what switches between browser mode and spatial mode.

Anyway, if that doesn't solve your problem then you should simply delete (or move somewhere else until you confirm that it fixes the problem) nautilus's configuration files from root's home to reset all it's settings to defaults.
______________________________________________________________________

I disabled "Open each folder in it's own window", but that did not solve the problem. Nautilus is still screwed up.

Using Dolphin I looked in my home directory but I don't see any configuration files for nautilus. Where exactly are the nautilus configuration files? 

JBA2337

---

### Post by mcduck on 2010-07-21
Don't look at your home, you should be looking at root's home.. Try moving /root/.nautilus and /root/.gconf somewhere else to see if that solves the problem.

---

### Post by dcstar on 2010-07-21
> **JBA2337 said:**
> 
.......
Does anybody have an idea how to fix this problem?

JBA2337

This is my direct Nautilus root launcher command:

```
gksudo "dbus-launch nautilus --no-desktop --browser"
```

---

