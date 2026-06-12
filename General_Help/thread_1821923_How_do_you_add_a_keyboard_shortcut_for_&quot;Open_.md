---
title: "How do you add a keyboard shortcut for &quot;Open with Gimp&quot;?"
date: 2011-08-09
forum: General Help
---

### Post by bogdarnet on 2011-08-09
I'm using Image Viewer to go through a bunch of pictures and most of them need small fixes which I'm doing in GIMP.  At the moment, I'm going through the right-click menu to open them in GIMP, but I wondered if there was an easy way to add a keyboard shortcut to do this.  (Think I figured out how to make a keyboard shortcut to open GIMP in general, but not sure how to do "Open With"...)

Thanks!

---

### Post by bogdarnet on 2011-08-09
I've made a shortcut by editing in gconf-editor to open GIMP... but is there a global variable for the currently selected file?

---

### Post by bogdarnet on 2011-08-09
Solved, sort of.  Haven't figured out how to add this capability globally, but it is available in gthumb.

Well, not really solved... gthumb has its own issues that are making it less than ideal for this project.  I'd really like a keyboard shortcut to work in Image Viewer (is this the same program as Eye of Gnome?)

---

### Post by bogdarnet on 2011-08-09
Okay, here's a workaround that I'm using now:

(it is Eye of Gnome, for some reason in some places it says "Image Viewer" but in the Configuration Editor, it's eog)

changed the external editor from fspot to gimp.desktop, and now I can use the button in the toolbar rather than the right-click menu... seems about as economic as a keyboard shortcut

---

### Post by thefasterblueone on 2011-08-09
Is 'shift+F10' what you are looking for:confused:

---

### Post by bogdarnet on 2011-09-07
> **thefasterblueone said:**
> Is 'shift+F10' what you are looking for:confused:

Didn't know about that (shift+F10 for the right-click context menu... that's useful, but it wasn't exactly what I was trying to get at the time... 

finished that project though, so it's not important now, but what I was trying to get at the time was a way to select an image file and then use one key-stroke combination to open it up in GIMP, either from anywhere in gnome or within eog... it seemed I was getting close in gconf-editor, but I never really got there.

---

### Post by pqwoerituytrueiwoq on 2011-09-07
@bogdarnet
thanks that is so much faster 
command line for what i did based on what bogdarnet said
```
gconftool-2 --type string --set /apps/eog/ui/external_editor "gimp.desktop"
```

---

