---
title: "Would you like to run or display this file?"
date: 2009-09-04
forum: General Help
---

### Post by Muscovy on 2009-09-04
I made a simple shell script and the "Would you like to run or display this file?" message is bugging me. Any way to disable it?

---

### Post by ad_267 on 2009-09-04
In the file browser, Edit - Preferences - Behaviour - Executable Text Files - Run executables when they are opened (or Edit if that's what you want).

I would select the edit option, and make a launcher for the script in the menu or on the desktop.

---

### Post by Muscovy on 2009-09-04
Thanks. Though question; will this mess up svgs? I'm pretty sure I have to click "view" to open them.

---

### Post by Muscovy on 2009-09-04
Yeah, it prevents me from easily opening svgs.

---

### Post by ad_267 on 2009-09-04
That's weird, your SVGs shouldn't be executable. I'd edit their properties to make them not executable.

---

### Post by Muscovy on 2009-09-05
That works... for single svgs.

---

### Post by ad_267 on 2009-09-05
Why are your SVGs executable in the first place? Where do you get them from?

You can run this command to make all your svg files non-executable:
```
find -iname *.svg -exec chmod -x {} \;
```

---

### Post by CatKiller on 2009-09-05
> **Muscovy said:**
> That works... for single svgs.

It's not like you need to do them all by hand.

```
chmod -x *.svg
``` will remove executable permissions from all SVG files in a directory. You can get more elaborate and use the *find* command if you want to do all SVG files in a bunch of sub-directories.

---

### Post by Muscovy on 2009-09-05
Is there an easy way to do it to all, versus everything in that folder?

---

### Post by mvaradharajan on 2009-09-05
we can also use 

'chmod 776 file_name'

---

### Post by CatKiller on 2009-09-05
> **Muscovy said:**
> Is there an easy way to do it to all, versus everything in that folder?

You mean like ```
find / -iname '*.svg' -exec sudo chmod -x {} \;
```This will find every file called something.svg from the / directory on down and (as root) remove executable permissions from it. I wouldn't really recommend it though. I haven't tested the command, either.

You haven't said where you're getting all these executable SVGs from, or why you want to edit them in a text editor anyway.

I would be tempted to find an SVG, right-click on it, select Properties and the Open With tab and select something more appropriate than a text editor to open them with. eog ("Image Viewer") (for viewing) or Inkscape (for editing) seem like much more sensible things to do with an SVG than changing the text by hand. But maybe that's just me.

---

### Post by ad_267 on 2009-09-05
> **Muscovy said:**
> Is there an easy way to do it to all, versus everything in that folder?

The command I posted previously will find all SVGs from anywhere in your home directory and make them non-executable. Is that not what you want? You shouldn't need to do this from the root directory /, only from your home directory.

---

### Post by Muscovy on 2009-09-05
The issue was it would only do any svgs that weren't in another folder. For example, that command wouldn't touch any svgs in ~/Pictures, so I would have to say ~/Pictures/*.svg to do them.
  Though I don't need it anymore, because my shell script was so simple I realised I could just make a custom launcher. Though I still wonder, is there a way to just tell shell scripts to execute only, without messing around with everything else?

---

### Post by CatKiller on 2009-09-05
> **Muscovy said:**
> The issue was it would only do any svgs that weren't in another folder. For example, that command wouldn't touch any svgs in ~/Pictures, so I would have to say ~/Pictures/*.svg to do them.

No you wouldn't. Well, for my trivial example you would. But *find* looks in all sub-directories too. It'd be a bit crap and useless if it didn't. By default, it keeps going until it runs out of sub-directories, although you can tell it to stop at a certain depth.

ad_267's command will find all SVGs from any sub-directory from the location that it's run. You can get it to do all sub-directories from another directory by specifying that directory, as I did with my / example.

---

### Post by ad_267 on 2009-09-05
> **CatKiller said:**
> No you wouldn't. Well, for my trivial example you would. But *find* looks in all sub-directories too. It'd be a bit crap and useless if it didn't. By default, it keeps going until it runs out of sub-directories, although you can tell it to stop at a certain depth.

ad_267's command will find all SVGs from any sub-directory from the location that it's run. You can get it to do all sub-directories from another directory by specifying that directory, as I did with my / example.

What he/she said. :)

---

