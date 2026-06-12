---
title: "Accidently Got Rid of Music and Picture Folders"
date: 2010-11-11
forum: General Help
---

### Post by laurenbanjo on 2010-11-11
Sorry for the stupid question, but:

I was dragging my music and picture folders (the ones located in the "Home" folder) into Docky, but I accidentally dragged them into the Downloads folder, and now they don't have the little picture inscriptions in them anymore. They're not in the Home folder anymore, either. 

How can I get it back so it's this "special" kind of folder back?

---

### Post by Ichido on 2010-11-11
Start up the Terminal and type "gksu nautilus", without the quotes, which will bring up the Nautilus File Manager in *root* mode.
Then do a search for the Folder you lost.
Be VERY CAREFUL while in the *root* Mode!
When you find the location, write it down and close Nautilus, then use the "Places" drop-down menu to start up Nautilus in *user* Mode to move the files/folder to where you want it.

---

### Post by laurenbanjo on 2010-11-11
I searched for both, and nothing is coming up. :/ 
Am I searching in the right place? I searched in the "root" with the home icon.

---

### Post by simpleeddie on 2010-11-11
Hey! Accidents happen, fortunately you are using a great operating system that makes it easy to recover from such mistakes!

Just move the folders back into the Home folder, and if the icons are gone, just right click on them and select the icon you want.

Currently I’m not using Ubuntu, so I can’t test to make sure this is correct, but I can’t see why it would be any more work than this

---

### Post by laurenbanjo on 2010-11-11
Hey, that worked ! I edited this post 'cause I thought I did it before, but I realized I tried dragging it to the side instead. Well, thanks! :)

---

### Post by mcduck on 2010-11-11
Just create new directories called Music and Pictures, and then edit the ~/.config/user-dirs.dirs -file and make sure it has following lines:
```

XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
```
After that log out and back again and the directories should work as before.

---

