---
title: "Tomboy global hotkeys not working in 10.10"
date: 2010-10-27
forum: General Help
---

### Post by uliz on 2010-10-27
Hi all, 

I recently upgraded to Ubuntu 10.10 (all the way from 8.04) and I can't seem to get Tomboys global hotkey bindings to work. In addition to Tomboys own settings, I have been messing with gconf-editor, but had no success there either. All I need is Alt+F11 combination to open the default note and I have no idea where to go next, thanks for your help in advance!

---

### Post by alecnmk on 2010-10-27
Hi,

Any success on this one?

---

### Post by xdaedalus on 2010-11-01
Same problem here. I'll post if I figure anything out.

---

### Post by jfred99 on 2010-12-06
This certainly worked in 10.04 and I loved being able to create a note with a keystroke.  

There is a bug report : [https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/685309](https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/685309)

If you're desperate you could try to revert to an older version: [http://projects.gnome.org/tomboy/download.html](http://projects.gnome.org/tomboy/download.html)

Think I'll wait and see but if someone tries reverting to the old version of tomboy (1.2) running 10.10 please post the results.  I assume it should work fine.

---

### Post by raztus on 2011-02-24
That bug is still unassigned, but as a workaround you can create a global keyboard shortcut (in gnome: system > preferences > keyboard shortcuts).

From the tomboy man page I see two useful commands:
```
tomboy --start-here
tomboy --new-note
```
Obviously a workaround, but it's better than nothing.

---

### Post by chad.davis on 2011-02-24
> **raztus said:**
> That bug is still unassigned, but as a workaround you can create a global keyboard shortcut (in gnome: system > preferences > keyboard shortcuts).
...
Obviously a workaround, but it's better than nothing.

Great tip. Thanks for that.

---

### Post by Habeouscorpus on 2011-02-24
I noticed that very thing today. Thanks for the workaround!

(I use it for school, so a one-keystroke would be helpful!)

---

### Post by uliz on 2011-03-01
This does the trick perfectly and I also learned to solve similar hotkey problems, which I most likely will encounter in the future :)

Obviously the command I used for my specific need (opening default note) was a bit different, but nevertheless only a minute of googling away, so thank you very much!

--open-note TITLE/URL

---

### Post by sa-mejia on 2011-04-08
For those of you who might need a more step by step procedure of how to activate the hotkeys using the workaround:

Go to system > preferences > keyboard shortcuts

Click on add (a new window shows up).

  Under name, write something like "tomboy-new"

  Under command write:  "tomboy --new-note"

There should npw be a new line created in the window of keyboard shortcuts (probably the last one) which is called tomboy-new.  Simply click where it reads "disabled" and press the key-combination you want to use.

Repeat the process writing with tomboy-search (command: "/usr/bin/tomboy --search", and tomboy-start (command: "/usr/bin/tomboy --start-here".

---

### Post by sa-mejia on 2011-04-08
For those of you who might need a more step by step procedure of how to activate the hotkeys using the workaround:

Go to system > preferences > keyboard shortcuts

Click on add (a new window shows up).

  Under name, write something like "tomboy-new"

  Under command write:  "tomboy --new-note"

There should npw be a new line created in the window of keyboard shortcuts (probably the last one) which is called tomboy-new.  Simply click where it reads "disabled" and press the key-combination you want to use.

Repeat the process writing with tomboy-search (command: "/usr/bin/tomboy --search"), and tomboy-start (command: "/usr/bin/tomboy --start-here").

It worked for me.

S.

---

### Post by gkkg on 2011-04-12
Another workaround is to add the tomboy applet to the gnome panel (right click the panel, click 'add', search for 'tomboy', drag to the panel). The shortcut keys will work again.

Now, the problem with that workaround will appear with an upgrade to 11.04, since the gnome-panel no longer exists. In 11.04 then, the keybindings workaround should be useful... 

BUT there is a problem with that one: if tomboy is already open, the command 'tomboy --start-here' (or other command) will be ignored. So if tomboy is closed, it works as expected. If it's open, the 'search all notes' window appears instead. 

Is there another command that can work to bring up the start-here note when tomboy is open?? any help would be appreciated ...

---

### Post by electronics45 on 2013-01-03
Tomboy can still be controlled via dbus.  Just assign the following command to your preferred shortcut:
```
qdbus org.gnome.Tomboy /org/gnome/Tomboy/RemoteControl org.gnome.Tomboy.RemoteControl.DisplayNote $(qdbus org.gnome.Tomboy /org/gnome/Tomboy/RemoteControl org.gnome.Tomboy.RemoteControl.CreateNote)
```

You'll also need to install "qdbus" if it's not already installed:
```
sudo apt-get install qdbus
```

---

