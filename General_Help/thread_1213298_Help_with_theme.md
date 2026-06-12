---
title: "Help with theme"
date: 2009-07-14
forum: General Help
---

### Post by dbyjazz on 2009-07-14
My problem is I'm trying to install a new theme (system > preferences > appearance)

Well, when I install the theme it says "GNOME Theme Mac4Lin_GTK_v0.4 correctly installed" but the theme doesn't pop up. Then when I try again it says "Installation for theme "**Mac4Lin_GTK_v0.4" failed.** Can't move directory over directory"

Then I tried going to my home folder and doing (ctrl+h) and deleting my .theme files and .icon files.

Still doesn't work when I try again.

any help would be greatly appreciated. Thanks

---

### Post by mCion on 2009-07-14
I'm not an expert but when you get this message: 
> Then when I try again it says "Installation for theme "Mac4Lin_GTK_v0.4" failed
is because themes (I've noticed) install once. 

Regarding your real question, depends on the theme you're installing.  This last week I've installed several.  Some themes are only for mouse icons or other partial stuff.  Check what it is.  If your theme was correctly installed the first time it should appear within the new "Custom" theme selected (click Customize).  Look around (Icons, or other tabs) to see if you find it.

If you want to reinstall it, once you find it, click the delete button, and then when you install them again you wont get the error message i mentioned at the beginning.  post what you find

---

### Post by dbyjazz on 2009-07-14
thanks for the help, but sadly it didn't work.

anyone else got any ideas?

if it helps, I'm trying to install the Mac4Lin_v0.4 theme

---

### Post by Gatemaze on 2009-07-14
try extracting the theme if it is zipped and then install it manually by copying it to your themes dir

```
cp <theme> ~/.themes
```

If this fails attempt to copy it into the system themes folder

```
sudo cp <theme> /use/share/themes
```

For the record I have it installed just fine in my sys.

---

### Post by dbyjazz on 2009-07-14
> **Gatemaze said:**
> try extracting the theme if it is zipped and then install it manually by copying it to your themes dir

```
cp <theme> ~/.themes
```

If this fails attempt to copy it into the system themes folder

```
sudo cp <theme> /use/share/themes
```

For the record I have it installed just fine in my sys.

for this part

```
<theme>
```

which file do I choose? As you can probably tell I'm a complete noob lol

---

### Post by Gatemaze on 2009-07-14
the name of the directory of the theme...

---

### Post by dbyjazz on 2009-07-14
Ya I don't think I'm doing it right.

it says 'No such file or directory'

this is what I'm typing, and once again sorry for the noobness lol

```
derek@derek-laptop:~$ sudo cp <Mac4Lin_GTK_Graphite_v0.4> /derek/share/themes
bash: Mac4Lin_GTK_Graphite_v0.4: No such file or directory
```

---

