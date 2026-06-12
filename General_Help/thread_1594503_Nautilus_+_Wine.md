---
title: "Nautilus + Wine"
date: 2010-10-12
forum: General Help
---

### Post by nagisa on 2010-10-12
So I have installed Wine not so long ago and noticed one very annoying thing...
How should first of all remove it from all files, because it appears on every file, EVERY! That just too much of hassle to remove it from everything.

Second : In Open With list there is a lot of applications from wine, all they are greyed out, so I can't delete them this way. Any other ways to do that?

---

### Post by 3Miro on 2010-10-12
Go to a file and select "properties". Then select "default application" to be something other than notepad (gedit is good). This will change that for all the files of that type, so you only have to do it for one file of each type.

---

### Post by nagisa on 2010-10-12
> **3Miro said:**
> Go to a file and select "properties". Then select "default application" to be something other than notepad (gedit is good). This will change that for all the files of that type, so you only have to do it for one file of each type.

And how much file types I have to go through you think? I just don't want to see that Notepad thingy, second problem is not so much of problem.

---

### Post by 3Miro on 2010-10-12
.txt and .ini should cover pretty much all of it (I just cannot think of another one).

Actually, you should probably leave the .ini files alone, they are windows files and notepad will probably do a better job than gedit.

Basically, if you do it once, it should be fine. You will still see "Notepad", but it will not be default one and it will be used only if you explicitly select it.

---

### Post by nagisa on 2010-10-12
> **3Miro said:**
> .txt and .ini should cover pretty much all of it (I just cannot think of another one).

Actually, you should probably leave the .ini files alone, they are windows files and notepad will probably do a better job than gedit.

Basically, if you do it once, it should be fine. You will still see "Notepad", but it will not be default one and it will be used only if you explicitly select it.

Neither of files are default, just as I said, I just want to remove that Notepad thingy from Open As... Ant in Open as notepad appears for every file!

---

### Post by WorMzy on 2010-10-12
[LIST=1]
[*]Press Alt+F2
[*]Type ```
nautilus .local/share/applications
```
[*]Look at the list of files for the ones that you don't want and select them
[*]Press Del on the keyboard or right-click on the files and choose "Move to wastebasket"
[/LIST]

The wine applications will probably have names like "wine-extension-html.desktop".

---

### Post by nagisa on 2010-10-12
> **WorMzy said:**
> [LIST=1]
[*]Press Alt+F2
[*]Type ```
nautilus .local/share/applications
```
[*]Look at the list of files for the ones that you don't want and select them
[*]Press Del on the keyboard or right-click on the files and choose "Move to wastebasket"
[/LIST]

The wine applications will probably have names like "wine-extension-html.desktop".

Thank you bunch, worked like charm! I managed to clear second problem by deleting everything from Edit Menus > Other.

---

