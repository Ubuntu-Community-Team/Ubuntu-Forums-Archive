---
title: "startup error."
date: 2009-07-31
forum: General Help
---

### Post by evworld on 2009-07-31
I screwed my desktop up and I am getting this error

Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/home_icon_name


I have my home folder name screwed up

---

### Post by decoherence on 2009-07-31
This command oughta fix it...

```
gconftool --type string -s /apps/nautilus/desktop/home_icon_name "$USER's Home"
```

That doesn't quite put it back the way it was (i'm not that good with gconftool) but it should be a reasonable solution.

Did you, by any chance, try to edit this key using the Configuration Editor tool? (aka gconf-editor) If so, it seems to me that gconf-editor defaults new values to int whereas this name should definitely be a string (hence the error message)

---

### Post by evworld on 2009-07-31
Here is how I screwed it up.

I had my home folder on my desktop.  I wanted to change the icon of my home folder.  I had a brain fart and changed it to Firefox icon.  After that I get the error.  I can't open my home folder from places on the pane.  If I go to desktop editor and uncheck the home visible I can open the home folder from panel.

---

### Post by evworld on 2009-07-31
> **decoherence said:**
> This command oughta fix it...

```
gconftool --type string -s /apps/nautilus/desktop/home_icon_name "$USER's Home"
```That doesn't quite put it back the way it was (i'm not that good with gconftool) but it should be a reasonable solution.

Did you, by any chance, try to edit this key using the Configuration Editor tool? (aka gconf-editor) If so, it seems to me that gconf-editor defaults new values to int whereas this name should definitely be a string (hence the error message)


That got me back with out error but I have my home folder icon as firefox icon.  How do I get my icon back to home icon?

---

### Post by decoherence on 2009-07-31
> **evworld said:**
> That got me back with out error but I have my home folder icon as firefox icon.  How do I get my icon back to home icon?

Good question... I would've thought there'd be a way to do this with gconf but I can't find it. All I can suggest is right clicking the icon, selecting Properties, clicking the icon in the window that comes up and setting a more appropriate icon. I believe the default is

/usr/share/icons/Human/scalable/places/user-home.svg

---

### Post by evworld on 2009-07-31
> **decoherence said:**
> Good question... I would've thought there'd be a way to do this with gconf but I can't find it. All I can suggest is right clicking the icon, selecting Properties, clicking the icon in the window that comes up and setting a more appropriate icon. I believe the default is

/usr/share/icons/Human/scalable/places/user-home.svg


Thanks for your help so far.  I believe to change the icon I need to do what you suggested.  But your path is not the right one.  

I have my home folder on my desktop now.  But if I use your path the icon looks like a folder.  I need it to look like a house...   I believe where ever the computer icon is stored I should find the home icon there too.   What do you think?   If so where would they be stored.

---

### Post by gastly on 2009-07-31
Try looking in the directory called '.icons' in your home dir. This is, I believe, where all the custom icon themes get stored.

---

### Post by decoherence on 2009-07-31
> **evworld said:**
> Thanks for your help so far.  I believe to change the icon I need to do what you suggested.  But your path is not the right one.  

I have my home folder on my desktop now.  But if I use your path the icon looks like a folder.  I need it to look like a house...   I believe where ever the computer icon is stored I should find the home icon there too.   What do you think?   If so where would they be stored.

Somewhere in /usr/share/icons/ I would imagine. Pick whatever one you like.

---

### Post by kittyrin on 2009-07-31
I'm having problems starting my Ubuntu. 
I recently loaded the latest version, and all was functioning, but now I'm having difficulty just getting it to start.

It will tell me Ubuntu is running in low-graphics mode
Errors: 
(EE)NV(0): couldn't find the DDC routing table.
(EE)Screen(s) found, but none have a usable configuration.
:(

---

