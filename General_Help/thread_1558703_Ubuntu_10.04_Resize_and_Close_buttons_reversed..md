---
title: "Ubuntu 10.04 Resize and Close buttons reversed."
date: 2010-08-22
forum: General Help
---

### Post by Garetty on 2010-08-22
The close, minimize, and resize buttons are all on the left side, which I like. But recently I've noticed that the Close and Resize buttons are switched. How can I fix this?

Click the picture so you can see it.
[[IMG]http://img695.imageshack.us/img695/6198/selection001p.th.png[/IMG]]("http://img695.imageshack.us/i/selection001p.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by PPPilot on 2010-08-22
The position of the window buttons may have changed if you installed a different theme. The easy way to fix the problem is to download Ubuntu Tweak at: [http://ubuntu-tweak.com](http://ubuntu-tweak.com) After you have it installed open it and on the left side under Desktop select Window Manager Settings. In the Main window the first item is Window Titlebar Button Layout. Select left and quit out. If you notice, right below the Left or Right choice, you choose custom and drag your buttons any where on the Title Bar. In addition Ubuntu Tweak does a lot of cool stuff in a nice easy to use GUI interface.

---

### Post by Forgotten Path on 2010-08-22
Without installing additional programs:

In a terminal:

```
brent@WassumR:~$ gconf-editor
```

Once the Configuration Editor opens, expand "apps" on the tree, find "metacity", expand it, and then click on the "general" folder. In the right hand pane, find "button_layout" and right-click it.  Choose "Edit Key", and change the key value to "maximize,minimize,close:". Click okay and the changes will happen right away. Then you can close the Configuration Editor and your terminal.

If you want the buttons moved back to the right side for some reason, follow the method in [this]("http://ubuntuforums.org/showpost.php?p=9217024&postcount=1") post, so you don't screw up future themes.

---

### Post by Garetty on 2010-08-22
> **Forgotten Path said:**
> Without installing additional programs:

In a terminal:

```
brent@WassumR:~$ gconf-editor
```Once the Configuration Editor opens, expand "apps" on the tree, find "metacity", expand it, and then click on the "general" folder. In the right hand pane, find "button_layout" and right-click it.  Choose "Edit Key", and change the key value to "maximize,minimize,close:". Click okay and the changes will happen right away. Then you can close the Configuration Editor and your terminal.

If you want the buttons moved back to the right side for some reason, follow the method in [this]("http://ubuntuforums.org/showpost.php?p=9217024&postcount=1") post, so you don't screw up future themes.
That worked. Thanks.

> **PPPilot said:**
> The position of the window buttons may have  changed if you installed a different theme. The easy way to fix the  problem is to download Ubuntu Tweak at: [http://ubuntu-tweak.com]("http://ubuntu-tweak.com/")  After you have it installed open it and on the left side under Desktop  select Window Manager Settings. In the Main window the first item is  Window Titlebar Button Layout. Select left and quit out. If you notice,  right below the Left or Right choice, you choose custom and drag your  buttons any where on the Title Bar. In addition Ubuntu Tweak does a lot  of cool stuff in a nice easy to use GUI interface.
I would have tried that but F P's looked easier. Thanks anyways. ;)

---

### Post by Forgotten Path on 2010-08-22
No problem, glad I could help.  :D

---

