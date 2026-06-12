---
title: "setting standard app for filetype with wine"
date: 2011-09-20
forum: General Help
---

### Post by gerdb on 2011-09-20
hi,

i like to set irfanview.exe as standard-app to image-files.

therefore i went to a image-file, right-clicked and chose "open with"

command. Then i wrote "wine "path/to/irfanview"" and started

but just the app startet, not the file, so 

How do i get the filename in "open with" commandline???

Pls help

thx in advance

---

### Post by Toz on 2011-09-20
Here is how I got this working. From a terminal window:

1. Create a file (in your home or bin directory for each application):
```
gksudo gedit ~/bin/OpenWithIrfanView
```

2. Paste in these contents:
```
#!/bin/bash

QUICKPARLOCATION="c:\\Program Files\\IrfanView\\i_view32.exe"
PARAM=`winepath -w "$*"`
wine "$QUICKPARLOCATION" "$PARAM"
exit 0

```

3. Save the file

4. Make the file executable:
```
chmod +x ~/bin/OpenWithIrfanView
```

5. Right-click on the file you want to open, select "Open With", choose "custom command", and locate this file.

You can create this type of association with any other program by simply copying the file, changing the QUICKPARLOCATION= line, and doing the same.

---

### Post by gerdb on 2011-09-20
hi,

seems to be working so thx for that,

but elegant is that not

the doubleclick on a file is emitting an event, 
with the filename as caller, 
so i like to get the caller's name to add to the called commandline scipt

maybe its something like "this->" or "$#~0123" or "SELF" or a makro or whatever the hell linux is working with

im very new to linux, but calling a script from a commandline (which is also a script) seems to be overloaded and unecessary to me.

thx

---

