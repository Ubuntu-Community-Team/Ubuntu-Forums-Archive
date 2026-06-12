---
title: "Deluge died of mysterious causes"
date: 2011-09-20
forum: General Help
---

### Post by Murdoc_of_puts on 2011-09-20
So I really don't know what happened.  One minute Deluge is working just fine, the next it won't load.  I've tried purging it and related files, and re-installing it to see if that fixed anything.  It didn't.  I'm getting the same error as before I reinstalled it.

Traceback (most recent call last):
  File "/usr/bin/deluge", line 9, in <module>
    load_entry_point('deluge==1.3.1', 'gui_scripts', 'deluge')()
  File "/usr/lib/pymodules/python2.7/deluge/main.py", line 121, in start_ui
    UI(options, args, options.args)
  File "/usr/lib/pymodules/python2.7/deluge/ui/ui.py", line 128, in __init__
    ui = GtkUI(args)
  File "/usr/lib/pymodules/python2.7/deluge/ui/gtkui/gtkui.py", line 217, in __init__
    self.torrentview = TorrentView()
  File "/usr/lib/pymodules/python2.7/deluge/ui/gtkui/torrentview.py", line 182, in __init__
    "torrentview.state")
  File "/usr/lib/pymodules/python2.7/deluge/ui/gtkui/listview.py", line 177, in __init__
    self.load_state(state_file)
  File "/usr/lib/pymodules/python2.7/deluge/ui/gtkui/listview.py", line 281, in load_state
    state = cPickle.load(state_file)
cPickle.UnpicklingError: invalid load key, ''.
 

is the print out from the terminal.  I don't know what a pickling error is.  Is that when you don't know what went wrong and you say "Well this sure is a pickle"?  Any one else have this happen to them?  Any help on this matter would be appreciated.

---

### Post by Cas07 on 2011-09-22
This is usually caused by a corrupt state file in your config so reinstalling would have no effect. Try with a fresh config. 

Deluge config location:
```
~/.config/deluge/
```

There is a bug report for this [#750146]("https://bugs.launchpad.net/ubuntu/+source/deluge/+bug/750146")

---

### Post by SpatryX on 2011-09-22
Thanks! That worked for me!

---

### Post by Murdoc_of_puts on 2011-09-23
yeah, that worked.  Thanks. I'll mark it as solved.  Just a question though, why when I purged deluge did it not take out the config file as well?  I thought that's what purge was supposed to do.

---

### Post by Cas07 on 2011-09-24
> why when I purged deluge did it not take out the config file as well? I thought that's what purge was supposed to do.

apt will not touch anything in your home directory as that could have unintended consequences.

---

### Post by Murdoc_of_puts on 2011-09-25
good to know, thanks.

---

