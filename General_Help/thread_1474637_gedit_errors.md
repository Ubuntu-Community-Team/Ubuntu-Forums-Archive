---
title: "gedit errors"
date: 2010-05-06
forum: General Help
---

### Post by rock4christ on 2010-05-06
whenever i run gedit in the terminal, i can edit and save a file, but when i close it, i get

```
(gedit:1902): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

(gedit:1902): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

(gedit:1902): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

```

is something broken in my gedit?

---

### Post by dcstar on 2010-05-07
> **rock4christ said:**
> whenever i run gedit in the terminal, i can edit and save a file, but when i close it, i get

```
(gedit:1902): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

(gedit:1902): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

(gedit:1902): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

```

is something broken in my gedit?

Gedit is not supposed to be run from a terminal, don't worry about things that actually work correctly even though you don't use them correctly.

---

### Post by rock4christ on 2010-05-07
> **dcstar said:**
> Gedit is not supposed to be run from a terminal, don't worry about things that actually work correctly even though you don't use them correctly.

so im not supposed to sudo gedit /path/to/file.ext? 

as a curious side question, is there a way to add a 'run as root' command to the right click menu?

---

### Post by piratebill on 2010-05-07
> **rock4christ said:**
> so im not supposed to sudo gedit /path/to/file.ext? 

If you want to edit files using the command line, I'd just use vim.

---

### Post by finlost on 2010-05-07
> **rock4christ said:**
> so im not supposed to sudo gedit /path/to/file.ext? 

as a curious side question, is there a way to add a 'run as root' command to the right click menu?
Use *gksu edit /path/to/file.ext*

---

### Post by SPr on 2010-05-07
> **dcstar said:**
> Gedit is not supposed to be run from a terminal, don't worry about things that actually work correctly even though you don't use them correctly.

There is absolutely nothing wrong with starting it from the CLI. Just because it's a Gnome app doesn't mean that it should only be started by clicking it's icon. Why do you think this is the wrong method to start a program?

I assume [https://bugs.launchpad.net/ubuntu/lucid/+bugs](https://bugs.launchpad.net/ubuntu/lucid/+bugs) is the correct place to report bugs (you don't say which version of Ubuntu you have). Search first to see if the bug is already there.

---

### Post by arpanaut on 2010-05-07
There are good reasons why [COLOR="Red"]not[/COLOR] to start graphical programs with sudo from the terminal:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by SPr on 2010-05-07
> **arpanaut said:**
> There are good reasons why [COLOR="Red"]not[/COLOR] to start graphical programs with sudo from the terminal:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

I didn't say there wasn't problems with starting a GUI app with root privs by using sudo. I said that starting a GUI app from a terminal is absolutely fine.

I would love to know why someone reckons that using the terminal to start a GUI app is wrong.

---

### Post by arpanaut on 2010-05-07
Nothing wrong with starting graphical prog. from terminal. Just do it correctly for root with gksu or gksudo to avoid the possible problems mentioned in the article.

No biggie, after all it's your rig...:mrgreen:

---

### Post by oldos2er on 2010-05-07
> **rock4christ said:**
> is there a way to add a 'run as root' command to the right click menu?

```
sudo apt-get install nautilus-gksu
```

---

