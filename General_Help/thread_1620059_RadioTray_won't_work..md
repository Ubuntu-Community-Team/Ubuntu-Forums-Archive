---
title: "RadioTray won't work."
date: 2010-11-12
forum: General Help
---

### Post by ivarn on 2010-11-12
Hey. I use RadioTray a lot, but now for some reason it will no longer work.
It doesn't show up on the system tray as usual and I got these errors when I checked it in the terminal;
> Traceback (most recent call last):
  File "/usr/bin/radiotray", line 8, in <module>
    radiotray.main(sys.argv[1:])
  File "/usr/lib/pymodules/python2.6/radiotray/radiotray.py", line 33, in main
    RadioTray()
  File "/usr/lib/pymodules/python2.6/radiotray/RadioTray.py", line 61, in __init__
    self.systray = SysTray(self.mediator, self.provider, self.log)
  File "/usr/lib/pymodules/python2.6/radiotray/SysTray.py", line 83, in __init__
    self.update_radios()
  File "/usr/lib/pymodules/python2.6/radiotray/SysTray.py", line 230, in update_radios
    self.provider.walk_bookmarks(self.group_callback, self.bookmark_callback, self.radioMenu)
  File "/usr/lib/pymodules/python2.6/radiotray/XmlDataProvider.py", line 291, in walk_bookmarks
    self.walk_bookmarks(group_func, bookmark_func, new_user_data, group + "/group[@name='"+ child_name +"']")                
  File "/usr/lib/pymodules/python2.6/radiotray/XmlDataProvider.py", line 293, in walk_bookmarks
    bookmark_func(child_name, user_data)
  File "/usr/lib/pymodules/python2.6/radiotray/SysTray.py", line 256, in bookmark_callback
    if radio_name.startswith("[separator-"):
AttributeError: 'NoneType' object has no attribute 'startswith'
So what do I do here?
Can somebody plz help me with this?
Thanks in advance :)

---

### Post by ivarn on 2010-11-12
Bug fixed by me :)
I checked the bookmark file (/home/username/.local/share/radiotray/), and for some reason, when I add more than x # of radio stations, the <bookmark!> duplicates after each other instead of before the radio station name and url. Oh well. Problem solved :)
But this bug should be fixed. I mean I was just lucky and checked the file.
EDIT: Example; <bookmark!><bookmark!><bookmark!>

---

### Post by saradisn on 2010-11-17
I have the same problem with radiotray. 

Edit: I opened it with the text editor and erased  the two extra "<bookmark!>" and left one , as ivarn did. Its OK now.

---

