---
title: "Command line &quot;gnome-open&quot;"
date: 2012-02-01
forum: General Help
---

### Post by Chough39 on 2012-02-01
I am using Ubuntu 11.10 and GNOME 3.2.1. on a Dell Inspiron 1501



When I use the command "gnome-open" as below, the file opens but I am left with the following message Gtk-WARNING. Perhaps someone would be kind enough to enlighten me as to why this occurs and how it may be stopped.
 

 gerald@gerald-desktop:~/Documents$ gnome-open reactions.odt  
 gerald@gerald-desktop:~/Documents$  
 (soffice:2286): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

---

### Post by MG&amp;TL on 2012-02-01
Gtk is the toolkit behind the GNOME (Unity is modified GNOME) desktop. It has recently had a big overhaul, this is probably why this warning has occurred. 

It does not do any harm whatsoever, as far as I know. For more information, and to fix, see [here]("http://askubuntu.com/questions/66356/gdk-gtk-warnings-and-errors-from-the-command-line") and install the gtk2-engines-pixbuf package:

```
sudo apt-get install gtk2-engine-pixbuf
```

Hope this helps.

---

### Post by Chough39 on 2012-02-06
Thanks for the help. I installed   [FONT=Andale Mono]gtk2-engines-pixbuf[/FONT]    from Synaptic Package Manager and the problem is now solved.

---

