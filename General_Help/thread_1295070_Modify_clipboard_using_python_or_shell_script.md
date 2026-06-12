---
title: "Modify clipboard using python or shell script?"
date: 2009-10-19
forum: General Help
---

### Post by growthmetal on 2009-10-19
I was getting really sick of using shift-control-c instead of the usual control-c to copy stuff from my terminal.  But control-c is also the terminal's interrupt code.  So I changed the terminal options so that control-c copied and then wrote an extremely short program that would display the interrupt code in my terminal so I could copy and paste it into the offending process.  I'd like to know how I can make my program even more useful by having it put the interrupt code directly into the clipboard.  Any idea how to do this?

---

### Post by Lars Noodén on 2009-10-19
Are you aware that clicking the middle button of the mouse will transfer the highlighted text?  No need to involve the other hand at all.

---

### Post by VCoolio on 2009-10-19
You can install and use xclip:
```
echo "whatever you need in your clipboard" | xclip
```

Or with python:

```
#!/usr/bin/python

import pygtk
pygtk.require('2.0')
import gtk

# get the clipboard
clipboard = gtk.clipboard_get()

# set the clipboard text data
clipboard.set_text("%s" % (clipboardtext))

# make our data available to other applications
clipboard.store()
```

---

