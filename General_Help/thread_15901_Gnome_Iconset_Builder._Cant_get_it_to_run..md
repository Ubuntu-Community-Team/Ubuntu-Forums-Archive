---
title: "Gnome Iconset Builder. Cant get it to run."
date: 2005-02-17
forum: General Help
---

### Post by MetalMusicAddict on 2005-02-17
I wanna make some Gnome icon themes so I googled and found "Gnome Iconset Builder". [LINK](http://unix.freshmeat.net/projects/gib_/). I was happy that I could apt it but after it installs it gives me this in the terminal: ```
(<unknown>:7000): libglade-CRITICAL **: file glade-xml.c: line 1198 (glade_xml_build_interface): assertion `wid != NULL' failed

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00215> Gib:.ctor ()
in <0x00020> gib.MainClass:Main (string[])
```
Dont know what to make of it.  ](*,)

---

### Post by MetalMusicAddict on 2005-03-28
Do we have themers here? Anyone gotten GIB to work?

---

### Post by kassetra on 2005-03-28
[QUOTE=MetalMusicAddict]Do we have themers here? Anyone gotten GIB to work?[/QUOTE]

Hmmm... as far as I know that's a glade issue...  I used GIB on my system previously, but I didn't have this error...
The window name used in the app has to be the same as the one given to the window in glade -- so when it's not, it gives you that error...

Can you edit the .glade files?  You might also have to edit the .mono or whatever they are called...

You're looking for something like this line in the .glade file:
```
widget class="GtkWindow" id="window1"
```

And you want to make sure you have a matching window name in the .mono (or whatever) file... so you're looking for something like this:
```
windowname="window2"
``` 
You'd want to change the "window2" to be "window1" so that it matches the .glade file.

---

