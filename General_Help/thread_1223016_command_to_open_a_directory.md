---
title: "command to open a directory"
date: 2009-07-25
forum: General Help
---

### Post by otz070 on 2009-07-25
ok this should be real easy, but I cannot seem to find an answer.

what I want to do is use obmenu to create something like a places menu. so basically I want to make links to my most common directories.

only problem is under execte I put something like /home/user/documents 
it don't work. what do I have to do to make it so it actually opens that folder?

Thanks:D

---

### Post by bacil on 2009-07-25
```
cd /home/Dir 
```

---

### Post by DaithiF on 2009-07-26
Not sure if I interpreted the original question correctly, but I thought the poster was asking how to open directories in a file browser, effectively so that they could create customised places menu for their particular directory structure.

if so, the command would be:
nautilus /path/to/directory

e.g. 
nautilus /home/username/Photos
nautilus /home/username/Movies
etc

cheers

---

### Post by VCoolio on 2009-07-26
Since the question is about obmenu I assume you run an alternative window manager so you don't want nautilus to draw your desktop (if you're using nautilus at all, I'd say use thunar or pcmanfm or emelfm2), so then you'll need nautilus --no-desktop /path/to/folder.

---

### Post by otz070 on 2009-08-04
ok see the attachment for a picture of what I'm trying to do
I want to ope a line such as this from the open box menu in pcmanfm so I can see the files (as you normally would.)
```
~/.local/share/Trash/files/
```
So the problem is what [COLOR="Red"]prefix[/COLOR]/[COLOR="Red"]suffix[/COLOR] do I add to this to get it to open from the [COLOR="Red"]openbox menu[/COLOR] as a normal directory???

Hopefully this better explains it?:)

to the best of my knowledge nautilis is running during my openbox session:)

Thanks:)

---

### Post by 3rdalbum on 2009-08-04
> **otz070 said:**
> ok see the attachment for a picture of what I'm trying to do
I want to ope a line such as this from the open box menu in pcmanfm so I can see the files (as you normally would.)
```
~/.local/share/Trash/files/
```
So the problem is what [COLOR="Red"]prefix[/COLOR]/[COLOR="Red"]suffix[/COLOR] do I add to this to get it to open from the [COLOR="Red"]openbox menu[/COLOR] as a normal directory???

You put the name of the file manager, then a space, then the directory you want it to open.

```
pcmanfm ~/.local/share/Trash/files/
```

---

### Post by otz070 on 2009-08-04
ok sweet!
Thanks so much:D

---

