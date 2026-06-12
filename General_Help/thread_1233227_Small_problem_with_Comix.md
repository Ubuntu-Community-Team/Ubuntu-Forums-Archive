---
title: "Small problem with Comix"
date: 2009-08-06
forum: General Help
---

### Post by utaku_ryukko on 2009-08-06
Hello all,

I'm using Comix to read some archives. Until two weeks ago, everything was OK. Since I can't open an archive when Comix is launched, either with File-->Open or Ctrl+O.
I've got no problem when going into Nautilus and then right-click then Open with Comix.


When opening Comix in a terminal, I've got the following return:
Traceback (most recent call last):
  File "/usr/share/comix/src/filechooser.py", line 269, in open_main_filechooser_dialog
    _main_filechooser_dialog = _MainFileChooserDialog(window)
  File "/usr/share/comix/src/filechooser.py", line 166, in __init__
    _ComicFileChooserDialog.__init__(self)
  File "/usr/share/comix/src/filechooser.py", line 90, in __init__
    if os.path.isdir(prefs['path of last browsed']):
  File "/usr/lib/python2.6/genericpath.py", line 41, in isdir
    st = os.stat(s)
TypeError: coercing to Unicode: need string or buffer, NoneType found

I was asked to do the following modification in filechooser.py:
**Code:**

        _print prefs['path of last browsed']_
        if os.path.isdir(prefs['path of last browsed']):
            self.filechooser.set_current_folder(prefs['path of last browsed'])
        self.show_all()

The return of the print is: None

Any idea where this little bug is coming from and how I can solve it?

Many thanks in advance

---

