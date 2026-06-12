---
title: "window without decoration"
date: 2010-08-23
forum: General Help
---

### Post by gufide on 2010-08-23
Hi, there anyway to make a window without decoration? (borders, button...). It don't having this feature in window rule in compiz. It is just for one program, to solve a bug with it. Thanks

---

### Post by Dustin2128 on 2010-08-23
I had this problem myself, and it appears that you can't do it on a window by window basis on gnome. You can do it, however, with kde. You can also use compiz fusion icon to integrate the two desktop environments, but that was too ungainly so I just swapped to kde. If it's temporary though, its not too bad.

---

### Post by gufide on 2010-08-23
But it have anyway to make that a program open without window like in window rule? in the command line of compiz?

---

### Post by Dustin2128 on 2010-08-23
> **gufide said:**
> But it have anyway to make that a program open without window like in window rule? in the command line of compiz?
are you asking for a configuration to make sure the program never opens with window decor? There's probably a command for that somewhere, I'll google it if I got what you're asking right :)

---

### Post by Ginsu543 on 2010-08-23
You can do it in Gnome just fine, as long as you have Compiz enabled. If you haven't already, download and install CompizConfig Settings Manager (also compiz-fusion-plugins-extra). Open the Manager and click on Window Decoration. Go down to the "Decoration windows" setting and add the window you want without decoration using the ! command.

For example, my Terminal window has no window decorations. To get this, I typed in:
```

(any) & !(class=Gnome-terminal)

```This will remove the window decoration from the Gnome Terminal. You can keep stringing along other windows you don't want decorations for:
```

(any) & !(class=Gnome-terminal) & !(class=Vlc) & !(title=VLC (XVideo output)) & !(class=Totem)

```

You can see the result of these commands on my Desktop:

---

### Post by gufide on 2010-08-24
Ho, thank you very much! It will be very useful.

---

### Post by gufide on 2010-08-24
Just another question, how did you get this apperance Ginsu543?

---

### Post by Ginsu543 on 2010-08-24
You'll have to be more specific since I have many customizations in place, including Conky, Tint2, custom icon set, and gtk-2.0 themes such as Dyne and Kupo Finale Dark.

---

