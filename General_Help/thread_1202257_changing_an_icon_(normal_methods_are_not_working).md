---
title: "changing an icon (normal methods are not working)"
date: 2009-07-02
forum: General Help
---

### Post by Hybrid86 on 2009-07-02
I've recently installed the shiki-colors theme in ubuntu, and was looking to change the user switcher icon. No big deal right?

The icon is marked as "application-exit.png", and I already have the icon I want to replace it with ready, so use "sudo nautilus" to get into the /usr/share/icons/(and so on) and replaceed the icon. After logging back in however, the icon remained. Confused, I went to my home folder, and found there was a ".icons" folder where the icons were also installed. figuring that was it, I replaced the "application-exit.png" icon there as well.

STILL no dice. Confused even more now, I did a search oh my pc for the filename. The only shiki-color ones I could find were the ones I already replaced.


Any thoughts? Clearly there is something obvious I'm missing :/

---

### Post by trojanfoe on 2009-07-02
I don't understand how you could replace an icon in /usr/share/icons as the nautilus user; all the icons appear to be owned by root.  I suspect you didn't replace the icon, but simple added a new icon which is being ignored?

Edit: that's rubbish isn't it; you sudo'd nautilus to root, and not sudo'd to nautilus.  Oops sorry :/

---

### Post by redsoxreed on 2009-07-02
Did you remember to reboot or at least restart X after you changed the icons?

---

### Post by Hybrid86 on 2009-07-02
Well it did ask me if I wanted to replace the Icon, and all its shortcuts changed as well, so I'm assuming it didn't just make a new one.

EDIT:
And yes, I've rebooted.

---

### Post by trojanfoe on 2009-07-02
Yes you can do that - it confused me however as I always start a terminal and do 'sudo bash' to any kind of admin.

---

### Post by CatKiller on 2009-07-02
> **Hybrid86 said:**
> The icon is marked as "application-exit.png"

Are you sure? I'm pretty sure that the icon you want to change is gnome-logout. 16x16 for the panel applet. You don't need to reboot; just change theme and change back again.

Oh, and you should use **gksudo nautilus** rather than sudo nautilus.

---

### Post by Hybrid86 on 2009-07-02
> **CatKiller said:**
> Are you sure? I'm pretty sure that the icon you want to change is gnome-logout. 16x16 for the panel applet. You don't need to reboot; just change theme and change back again.


In this particular theme, it's named "application-exit.png"

---

### Post by CatKiller on 2009-07-02
> **Hybrid86 said:**
> In this particular theme, it's named "application-exit.png"

That makes no sense. There may be another file called application-exit, and it may look the same, but the file that the panel applet uses is gnome-logout. If the theme you're using doesn't have that icon, then the equivalent icon from the theme that's Inherited will be used instead.

---

### Post by Hybrid86 on 2009-07-02
I should have speicifed, Gnome-logout is there, but it is only a link to another png image. the png image it links to is "application-exit.png"

Perhaps this has something to do with the icon cache?

EDIT: Finally got the icon changed. For anyone else who finds this thread, here's how I did it:


1. replace the icons in both paths specified in my first post.

2. open the terminal and input the following four commands:
```

gtk-update-icon-cache
cd ~/.icons
gtk-update-icon-cache ICONSETNAMEHERE
killall gnome-panel

```
And that's it! enjoy your new Icon.


Now if only I could get my sound working... [http://ubuntuforums.org/showthread.php?p=7548462]("http://ubuntuforums.org/showthread.php?p=7548462")

---

### Post by CatKiller on 2009-07-02
> **Hybrid86 said:**
> I should have speicifed, Gnome-logout is there, but it is only a link to another png image. the png image it links to is "application-exit.png"

That makes a lot more sense. Glad you got it changed.

---

