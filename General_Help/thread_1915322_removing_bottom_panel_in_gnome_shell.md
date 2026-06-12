---
title: "removing bottom panel in gnome shell"
date: 2012-01-26
forum: General Help
---

### Post by Pro$pect on 2012-01-26
I am trying to remove the bottom panel in gnome shell so I found this extension([http://ubuntu.igameilive.com/2012/01/how-to-remove-bottom-panel-message-tray.html#comment-form](http://ubuntu.igameilive.com/2012/01/how-to-remove-bottom-panel-message-tray.html#comment-form)) that i've seen a few people using but for some reason it won't install using gnome tweak tool, when I try to its not even visible in the file explorer. Any other ways of doing this?

---

### Post by lolpenguin on 2012-01-26
Move the directory conta0ining extension.css metadata.json (and anything else) and move it to ~/.local/share/gnome-shell/extensions/ (or /usr/share/gn ome-shell/extensions/ if you want it available to everyone)
If it doesn't work you are probably using a different versions of GNOME Shell than the extensions was written for. Check the version number in metadata.json matches your version number.

---

### Post by Pro$pect on 2012-01-26
Checked the metadata says it works with 3.2 so I moved it over to that directory, restarted gnome and checked gnome tweak and it still isn't showing up.

---

### Post by Pro$pect on 2012-01-28
any other ways to remove the bottom panel?

---

### Post by sanderd17 on 2012-01-28
can you do ALT+F2 and execute the command

```

lg

```

There you have a tab with extensions. Does the extension you have installed show up?

Oh, and the directory you put it under should be ```
remove_bottom_bar@k2z.com
```, I hope you took that name.

---

### Post by sanderd17 on 2012-01-28
I just tried to install it (GS 3.2.2) and it works without problems. But that does mean I lose my notifications.

---

### Post by cbowman57 on 2012-01-28
The OP might be a better candidate for Cinnamon with the top panel only option.

Disabling the message tray in gnome-shell probably isn't practical at this time.

---

### Post by Pro$pect on 2012-01-28
> **sanderd17 said:**
> 
Oh, and the directory you put it under should be ```
remove_bottom_bar@k2z.com
```, I hope you took that name.

this is what got it to work for me, thanks.

---

### Post by sanderd17 on 2012-01-29
> **cbowman57 said:**
> The OP might be a better candidate for Cinnamon with the top panel only option.

Disabling the message tray in gnome-shell probably isn't practical at this time.

Unless you use an alternative notification area. I believe AWN does provide one. But that would mean you have to disable the notification area of GS first (and I'm not sure, but I think the extension is only hiding it, not disabling).

---

### Post by cbowman57 on 2012-01-29
> **sanderd17 said:**
> Unless you use an alternative notification area. I believe AWN does provide one. But that would mean you have to disable the notification area of GS first (and I'm not sure, but I think the extension is only hiding it, not disabling).

Good point, I hadn't considered that as a possibility.

---

