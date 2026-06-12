---
title: "Mass Rename"
date: 2010-11-27
forum: General Help
---

### Post by gannggstaz on 2010-11-27
I have a folder full of files, whose filenames fit in this format
```
Dead Kennedys - 1980 - Fresh Fruit For Rotting Vegetables  [www.Anarcho-Punk.net]
```
I want to remove "Dead Kennedys" and "[www.Anarcho-Punk.net]"from the files without having to go through each individually. I didn't understand how to use mmv or rename in this instance so I'm looking for any solution that works. I'd also like an explanation of what the script does and how it does this, because I want to do the same to other directories and will need to change the script for the appropriate filenames.

---

### Post by Wobblybob on 2010-11-27
You could just install a GUI app so you can preview the change before you make it. I use pyRenamer and Krename although the 2nd is a KDE app it runs on Gnome and both are in the repos.

---

### Post by sisco311 on 2010-11-27
Well, something like:
```
rename -n 's/Dead Kennedys - (.*)  \[www\.Anarcho-Punk\.net\]/$1/' ./*
```
should do the trick.

For some examples check out:
[http://ubuntuforums.org/showpost.php?p=5210607&postcount=2](http://ubuntuforums.org/showpost.php?p=5210607&postcount=2)
and a good sed or perl tutorial.


If you are not comfortable with the CLI tools, try one of the GUI ones:
[list]
[*]thunar (file manager)
[*]**gprename** 
[*]purrr 
[*]pyrenamer 
[*]gwenrename 
[*]**krename** 
[/list]

thunare, gprename and krename are easy to use, but still powerful.

---

### Post by Enigmapond on 2010-11-27
> **Wobblybob said:**
> You could just install a GUI app so you can preview the change before you make it. I use pyRenamer and Krename although the 2nd is a KDE app it runs on Gnome and both are in the repos.

Yep..:p EasyTag is another but they all work pretty well.

---

### Post by gannggstaz on 2010-11-27
Thanks, I didn't know such a thing existed. I'll see if it works.

---

### Post by ngrieb on 2010-11-27
There are also other GUI apps such as Gprename in the repos. ;)

---

### Post by gannggstaz on 2010-11-27
[http://wiki.redbrick.dcu.ie/mw/Mass_Renaming_Files](http://wiki.redbrick.dcu.ie/mw/Mass_Renaming_Files)
Actually I found this guide most helpful. I didn't achieve the rename in one clean step but I did remove the start and end as I wanted to in the first place, and it was easy.+

---

