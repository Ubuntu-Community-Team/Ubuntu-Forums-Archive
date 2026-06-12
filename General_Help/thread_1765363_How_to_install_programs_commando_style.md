---
title: "How to install programs commando style"
date: 2011-05-23
forum: General Help
---

### Post by oldarney on 2011-05-23
So I downloaded the Flash Projector
[http://download.macromedia.com/pub/flashplayer/updaters/10/flashplayer_10_sa_debug.tar.gz](http://download.macromedia.com/pub/flashplayer/updaters/10/flashplayer_10_sa_debug.tar.gz)

Any ideas on how to add links to the unity launcher?

After extracting the tarball the program ran fine. Thing is I don't want the executable or a link to it, on my desktop. I want to add it to the unity bar or the unity launcher. When I try to do that, unity grays out.

---

### Post by sj1410 on 2011-05-23
```


tar xzvf flashplayer_10_sa_debug.tar.gz
chmod a+x flashplayerdebugger
./flashplayerdebugger



```

---

### Post by oldarney on 2011-05-23
Thanks for the reply.

**I don't want to run it**! I just want to add it to the unity search and/or put it on the unity bar. Drag and drop fails epically on this one. :)

That code is to extract it, make it executeable and run it.

After downloading the package I opened with archive manager, put it on my desktop and double clicked it. Amazingly it ran, without any modifications.

---

### Post by prshah on 2011-05-23
> **oldarney said:**
> After extracting the tarball the program ran fine. I want to add it to the unity bar or the unity launcher. 

When the program is active, right click it's icon in the Unity bar and select "Keep in launcher" (or words to that effectt, don't remember the exact thing, since I'm not on Unity ATM).

Remember that changing the location AFTER creating the Unitybar shortcut will result in a dead shortcut.

---

### Post by oldarney on 2011-05-23
Yey prshah, that solves half the problem... but its not a program I use often, I don't want it in my main bar. My main concern is "how can I add it to the unity search launcher?"

---

### Post by prshah on 2011-05-23
> **oldarney said:**
> My main concern is "how can I add it to the unity search launcher?"
If you mean the list of programs, I have no idea how to add it to the main (first screen), but you can add it to the "More Apps" section by creating an entry in gnome's menu using alacarte (Unity reads Gnome Menus). Alt+F2, then```
alacarte
```

---

### Post by oldarney on 2011-05-23
> **prshah said:**
> (Unity reads Gnome Menus). Alt+F2, then```
alacarte
```

Alacarte... fun. How was I supposed to know this. It's a developer operating system and that's a power user feature, I shouldn't complain.

Thanks for your help.

---

### Post by mcduck on 2011-05-23
> **oldarney said:**
> Alacarte... fun. How was I supposed to know this. It's a developer operating system and that's a power user feature, I shouldn't complain.

Thanks for your help.

It's also appears in the System Settings, with the self explaining name of "Main Menu" and a tool tip describing it as "Change which applications are shown on the main menu".

So no, it's not a hidden power user feature that would require you to somehow know the right command, it's right there next to all your other settings. :)

---

### Post by prshah on 2011-05-23
> **oldarney said:**
> Alacarte... fun. How was I supposed to know this. It's a developer operating system and that's a power user feature, I shouldn't complain.


I'm more familiar with the command line than I am with the menus, especially Unity's menus. That's why I gave this advice. As explained by mcduck, it can be done via System-Preferences-Main Menu.

---

