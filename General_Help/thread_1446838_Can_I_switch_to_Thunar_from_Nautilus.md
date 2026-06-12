---
title: "Can I switch to Thunar from Nautilus?"
date: 2010-04-04
forum: General Help
---

### Post by Cam42 on 2010-04-04
I'm using Ubuntu Karmic, and I really don't like Nautilus. Is there a way to switch to Thunar?

---

### Post by Silent Warrior on 2010-04-04
Sure: 'sudo apt-get install thunar', or a package manager of your own choice. Then start Thunar from the menu. Simple as that. :)

Of course, if you want the shortcuts in the Places menu to start Thunar instead of Nautilus, you'll probably have to edit the menu to suit, but I'm not confident in my ability to properly walk you through that. Chances are, though, that if you try to remove Nautilus, you'll pull all of Gnome along with it. Let's not be hasty.

---

### Post by howefield on 2010-04-04
This worked a few months back for me when I was trying out dolphin. I expect it will work with Thunar.

Edit the following file after installing Thunar.

/usr/share/applications/nautilus-folder-handler.desktop and change nautilus --no-desktop %U to thunar.

Terminal command.

```
gksudo gedit /usr/share/applications/nautilus-folder-handler.desktop
```

You will want to make a backup of the file before editing.

---

### Post by MichealH on 2010-04-04
Well You could but keep nautilus as well, It draws the desktop unless you want no desktop I would keep both

---

### Post by NCLI on 2010-04-04
It's quite simple actually.

1) Install [Thunar]("apt:thunar")
2) Start gconf-editor and navigate to /->desktop->session->required_components
3) Replace the filemanager value with thunar.

This is the easiest, and official way.

---

### Post by Cam42 on 2010-04-04
Would I have to switch to xfce to completely get rid of Nautilus? That I wouldn't mind, I like how the desktop is managed in xfce better than in GNOME. The only thing holding me back is Docky's performance in xfce.

---

### Post by Silent Warrior on 2010-04-07
That depends on what you mean by getting rid of Nautilus. It's sort a central component in Gnome - no Nautilus, no Gnome file-manager nor desktop (I once read that it powers the desktop view as well - true?) - so just about everything in Gnome depends on it in some form or other, I guess. But just not using it, and setting GConf to use something else, it's not really as if you notice whether Nautilus is there or not, in terms of HD-space.
It's least trouble for you if you leave it alone.

---

### Post by Cam42 on 2010-04-11
After switching to Mint Helena, I've switched to thunar. It opens in everything but mintmenu. I'm digging through gconf-editor right now to try to fix that, but is there another way?

---

### Post by Simian Man on 2010-04-11
> **Cam42 said:**
> Would I have to switch to xfce to completely get rid of Nautilus? That I wouldn't mind, I like how the desktop is managed in xfce better than in GNOME. The only thing holding me back is Docky's performance in xfce.

Did you enable the xfwm compositor in "Window Manager Tweaks"?  Because with that, Docky shouldn't be any slower than it is under Gnome.

---

