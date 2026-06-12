---
title: "Where have my &quot;Places&quot; folders gone ?"
date: 2010-11-08
forum: General Help
---

### Post by grey1beard on 2010-11-08
I have been running Ubuntu 10.10 successfully on an amd64 system until about an hour ago.
I've just downloaded Rhodaforever 3d drawing software as a zip file, and not sure how to deal with a zip in ubuntu (Newbie immigrant from XP) tried several "Make new folder"/ copy to desktop, etc., attempts before I remembered how it was done in xp, and extracted the contents into a new folder, right clicked on it to open with Wine Windows program loader.
I then got an error window - File not found.

Next step was to access my file system in "Places", but each of the folders in the top half of the Places drop down menu now produce the same - "File not found" error window. 
I tried rebooting, hoping that would clear whatever glitch I'd generated, but to no avail.

All the entries in the lower half, from "Computer" down to "Recent Documents" work OK, as does everything else, as far as I have seen so far.
I can get at the file system by using the Computer selection etc., but can someone help me recover the correct working of the Places button.

Many thanks 
John

---

### Post by krtica on 2010-11-08
Try this:

```
gconftool-2 -s /desktop/gnome/url-handlers/file/command -t string "nautilus \"%s\""
gconftool-2 -s /desktop/gnome/url-handlers/file/enabled -t bool true
```

It helped me.

---

### Post by grey1beard on 2010-11-08
Thanks for the quick reply, krtica.
Can you give me a rough idea what those strings do (I presume I need to load both ?) as I'm not yet up to speed with command lines.
Regards
John

---

### Post by krtica on 2010-11-08
Oh, sorry.

You have to run terminal:
Applications -> Accessories -> Terminal

When it's open, just copy lines above and paste it in terminal.
(Hit enter to execute second line.)

Pasting in terminal is Ctrl+Shift+V

or

right click on terminal window -> paste

---

### Post by grey1beard on 2010-11-08
Well I'm d...ed. That's the fastest cure I've seen, and I didn't feel a thing.
Thanks again,
John

---

### Post by krtica on 2010-11-08
You are welcome, John.
Glad I helped.

Please, mark thread as "solved". :D

---

### Post by B-Mart on 2012-01-14
> **krtica said:**
> Try this:

```
gconftool-2 -s /desktop/gnome/url-handlers/file/command -t string "nautilus \"%s\""
gconftool-2 -s /desktop/gnome/url-handlers/file/enabled -t bool true
```

It helped me.
I have been looking all night for an answer, krtica, YOU. ARE. AWESOOOME.

---

