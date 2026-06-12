---
title: "Launcher icons"
date: 2011-09-03
forum: General Help
---

### Post by pederbruusgaard on 2011-09-03
Hi,
This has been briefly discussed in another [thread]("http://ubuntuforums.org/showthread.php?t=1836207"), but since that one was actually on a very different topic, I made a new one with a much less misleading title.

So, I've created a launcher in Ubuntu 11.04, and it's working fine, except for one thing: I can't pick my own icon. That is, I can edit the properties of the launcher and select exactly the one I want, and on the *desktop*, it stays that way (with the one I selected). But if I try to place it in the dock (or Launcher, as it's called, I just use dock to not confuse the two) the icon automatically switches back to one of the pre-installed default icons.

I have tried to move the icons I want into the folders where the default ones are:

```
peder@peder-ThinkPad-X220:~$ mv ~/Downloads/M8 usr/shared/icons/hicolor/scalable/apps
mv: cannot stat `/home/peder/Downloads/M8': No such file or directory
```

but as you can see, that didn't work. I suspect that is because I know very little of Ubuntu, so it might be a really silly trivial problem.

Thanks in advance for all help with this!

---

### Post by pederbruusgaard on 2011-09-03
Update:
Now I actually managed to copy the icon I want into the right folder, but it still doesn't work.
The only thing I can see that distinguishes it from the other icons is that it's a .png while the rest are .svg files. Gimp doesn't save as or export as .svg. Is there a way of achieving that?

---

### Post by Frogs Hair on 2011-09-03
> **pederbruusgaard said:**
> Update:
Now I actually managed to copy the icon I want into the right folder, but it still doesn't work.
The only thing I can see that distinguishes it from the other icons is that it's a .png while the rest are .svg files. Gimp doesn't save as or export as .svg. Is there a way of achieving that?

You can often just right click and rename the image . I have done this when changing my login icon with ubuntu tweak because an .svg required . Some images don't allow name change though .

---

### Post by pederbruusgaard on 2011-09-03
> **Frogs Hair said:**
> You can often just right click and rename the image . I have done this when changing my login icon with ubuntu tweak because an .svg required . Some images don't allow name change though .

Thanks for the suggestion! I tried it, but it still changes back to the default heart. I heart Mathematica, could have been worse :)

---

### Post by Frogs Hair on 2011-09-03
Make sure that you name the icon exactly the same as the original one . If you do that a dialog may appear asking if you want to replace the icon and if so , select yes . If you don't get a replace dialog you may have the wrong folder .

---

### Post by whatthefunk on 2011-09-03
Did you rename the old icon first?  If you cant change the name of the icon, make a symbolic link that has the .svg file extension.

---

### Post by pederbruusgaard on 2011-09-03
> **whatthefunk said:**
> Did you rename the old icon first?  If you cant change the name of the icon, make a symbolic link that has the .svg file extension.

Hi,
I could rename them, and I also managed to move them into place. The funny thing now is that I got one of the icons to stay, but not the other one. Thought that was kinda strange. I found both on the internet just now, and did the exact same things to them, renamed them and all. One thing I did notice, however, was that one of them all of a sudden turned into a root-owned sort of file. Under its properties -> Permissions, its owner is Root, apparently. Maybe that's why it worked. I don't know how I did that, though...

---

