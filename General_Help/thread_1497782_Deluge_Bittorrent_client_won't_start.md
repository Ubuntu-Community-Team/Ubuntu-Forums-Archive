---
title: "Deluge Bittorrent client won't start?"
date: 2010-05-31
forum: General Help
---

### Post by MusicMan374 on 2010-05-31
I don't know what exactly I did to wreck the functionality but something did Deluge in. I've purged the configuration files and libraries and reinstalled them three times over and every time in terminal that I start it using deluge-gtk I get the following output:

```
ryan@ryan-PC-Ubuntu:~$ deluge-gtk
Traceback (most recent call last):
  File "/usr/bin/deluge-gtk", line 9, in <module>
    load_entry_point('deluge==1.2.2', 'console_scripts', 'deluge-gtk')()
  File "/usr/lib/pymodules/python2.6/deluge/ui/gtkui/gtkui.py", line 107, in start
    Gtk().start()
  File "/usr/lib/pymodules/python2.6/deluge/ui/gtkui/gtkui.py", line 104, in start
    GtkUI(self.args)
  File "/usr/lib/pymodules/python2.6/deluge/ui/gtkui/gtkui.py", line 216, in __init__
    self.torrentdetails = TorrentDetails()
  File "/usr/lib/pymodules/python2.6/deluge/ui/gtkui/torrentdetails.py", line 116, in __init__
    state = self.load_state()
  File "/usr/lib/pymodules/python2.6/deluge/ui/gtkui/torrentdetails.py", line 432, in load_state
    state = cPickle.load(state_file)
cPickle.UnpicklingError: invalid load key, '&#65533;'.
ryan@ryan-PC-Ubuntu:~$ 

```

I can't seem to pinpoint whats causing all of this :confused:

---

### Post by wilee-nilee on 2010-05-31
I think I would run a purge again and then add the ppa and see if that doesn't work.
[https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

---

### Post by MusicMan374 on 2010-05-31
No dice.

I get this when using deluge command to start:

```
ryan@ryan-PC-Ubuntu:~$ deluge
Traceback (most recent call last):
  File "/usr/bin/deluge", line 9, in <module>
    load_entry_point('deluge==1.2.3', 'console_scripts', 'deluge')()
  File "/usr/lib/pymodules/python2.6/deluge/main.py", line 121, in start_ui
    UI(options, args, options.args)
  File "/usr/lib/pymodules/python2.6/deluge/ui/ui.py", line 128, in __init__
    ui = GtkUI(args)
  File "/usr/lib/pymodules/python2.6/deluge/ui/gtkui/gtkui.py", line 216, in __init__
    self.torrentdetails = TorrentDetails()
  File "/usr/lib/pymodules/python2.6/deluge/ui/gtkui/torrentdetails.py", line 116, in __init__
    state = self.load_state()
  File "/usr/lib/pymodules/python2.6/deluge/ui/gtkui/torrentdetails.py", line 432, in load_state
    state = cPickle.load(state_file)
cPickle.UnpicklingError: invalid load key, '&#65533;'.
```

---

### Post by 8Kuula on 2010-05-31
From error message I think state file is corrupted. So move all *.state files from ~/.config/deluge and try again.

---

### Post by MusicMan374 on 2010-05-31
I'm sorry, semi-newb here, can you elaborate a bit?

---

### Post by 8Kuula on 2010-05-31
way 1:
1) open home folder.
2) press ctrl+l (it is L ;)).
3) write: ~/.config/deluge to location bar.
4) move all .state files, should be 6 of them, to your desktop.
5) start deluge.

way 2:
1) open terminal
2) write (or copy & paste): mv ~/.config/deluge/*.state ~/Desktop/
3) start deluge.

edit:
To undo if won't work:
1) open terminal
2) write: mv ~/Desktop/*.state ~/.config/deluge/

---

### Post by IanW on 2010-05-31
Navigate to ~/.config/deluge (~/ is your /home/user folder, .config is a Hidden folder - If using Nautilus then right click in your /home/user folder and check "Show hidden files")
Create a folder with any name (I used "broken")
Move (not copy) any files ending in .state to the new folder
Restart Deluge

---

### Post by MusicMan374 on 2010-05-31
Moving the 6 in the config folder worked! There was one state file left in the ~/.config/deluge/state folder but that one isn't causing any startup issues. Thanks for your help, deluge is working now :)

---

### Post by ethan1701 on 2010-10-21
Encountered this problem recently, and this thread solved it.
Thanks!

-Ethan

---

