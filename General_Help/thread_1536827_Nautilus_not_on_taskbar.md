---
title: "Nautilus not on taskbar"
date: 2010-07-22
forum: General Help
---

### Post by Ultra_Man on 2010-07-22
When I open a nautilus file browser, it doesn't show up on my dockbarx applet. And the taskbar applet is also acting strange. It looks like I opened nautilus a million times. I'm using nautilus elementary.

---

### Post by M7S on 2010-07-23
In a terminal run:

```
dockbarx_factyory.py run-in-window
```
Start nautilus and then post the output from the terminal.


M7S,
DockbarX developer

---

### Post by Ultra_Man on 2010-07-23
It says command not found.

---

### Post by drewsus on 2010-07-27
> **Ultra_Man said:**
> It says command not found.

he meant: ***dockbarx_factory.py run-in-window***

I just started having this problem recently as well. 

Here is my output, after running the above command and then opening my home folder: 

```
Opened window matched with gio app on id: nautilus
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dockbarx/dockbar.py", line 476, in on_window_opened
    desktop_entry=desktop_entry)
  File "/usr/lib/pymodules/python2.6/dockbarx/dockbar.py", line 611, in make_groupbutton
    gb = GroupButton(identifier, desktop_entry, pinned)
  File "/usr/lib/pymodules/python2.6/dockbarx/groupbutton.py", line 201, in __init__
    self.update_name()
  File "/usr/lib/pymodules/python2.6/dockbarx/groupbutton.py", line 254, in update_name
    self.name = self.desktop_entry.getName()
  File "/usr/lib/pymodules/python2.6/xdg/DesktopEntry.py", line 43, in getName
    return self.get('Name', locale=True)
  File "/usr/lib/pymodules/python2.6/xdg/IniFile.py", line 103, in get
    value = gettext.dgettext(self.gettext_domain, self.content[group][key])
  File "/usr/lib/python2.6/gettext.py", line 545, in dgettext
    codeset=_localecodesets.get(domain))
  File "/usr/lib/python2.6/gettext.py", line 493, in translation
    t = _translations.setdefault(key, class_(open(mofile, 'rb')))
  File "/usr/lib/python2.6/gettext.py", line 180, in __init__
    self._parse(fp)
  File "/usr/lib/python2.6/gettext.py", line 313, in _parse
    v = v.split(';')
AttributeError: 'list' object has no attribute 'split'
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dockbarx/dockbar.py", line 400, in on_active_window_changed
    active_group = self.groups[active_group_name]
  File "/usr/lib/pymodules/python2.6/dockbarx/dockbar.py", line 97, in __getitem__
    raise KeyError, item
KeyError: u'nautilus'
```

---

### Post by M7S on 2010-07-27
Great, I forgot to subscribe to this thread. Sorry for not responding sooner.

The bug is not in dockbarx anyways. Gettext seems to have problem parsing a (wrongly formated) mo file or something. DockbarX shouldn't have to crash/behave odd just because it doesn't get a name for a launcher. I'll add some error handling. Thanks for the report.

---

### Post by drewsus on 2010-07-27
My pleasure! Ive been using dockbarx for some time now so any little bit I can do to help is exactly what I intend to do :)



[CENTER](\ /)
(O'o)
(> <)[/CENTER]

---

### Post by Vapourstreak on 2010-07-27
I had this problem also.  Twice, actually.  The first time, it was because I updated Dockbarx, so I removed the Dockbarx Repo and uninstalled it, and reinstalled the one on Gnome-look.org, and nautilus showed up again.

The second time, I tried the same thing, but it didn't work, and nautilus still never showed up, so I just installed docky.

---

### Post by drewsus on 2010-08-07
So any news on this M7S? I love dockbarx, but ive moved back to the regular window list because its pretty annoying not seeing nautilus windows? I have and use docky, but I like to use them in conjunction

---

### Post by M7S on 2010-08-08
A new version is out that hopefully fix this problem. It usually takes some time before the new version finds it way to the ppa, though.

---

### Post by drewsus on 2010-08-08
Fantastic, great to hear bunny man!

---

### Post by M7S on 2010-08-09
That bunny joke is getting really old, isn't it? My twist is no fun anymore since no one else seems to have bunny in their signatures.

---

### Post by drewsus on 2010-08-09
I dont know, do what you like. I liked it. I even flipped on above ^^

---

