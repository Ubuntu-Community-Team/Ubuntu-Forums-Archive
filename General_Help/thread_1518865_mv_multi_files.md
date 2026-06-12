---
title: "mv multi files"
date: 2010-06-27
forum: General Help
---

### Post by spiky001 on 2010-06-27
is it possible to move multiple files and folders at once in terminal?

---

### Post by dino99 on 2010-06-27
im pleased with click&drag

gnome-commander is a good tool (im afraid with this blind console method :lolflag:)

---

### Post by warfacegod on 2010-06-27
I agree with dino99. Stick with drag n' drop. Unless you are in a CLI only environment, the GUI is safer.

---

### Post by spiky001 on 2010-06-27
ok i,m still learning to use terminal so I will take your advice thks

---

### Post by dragos240 on 2010-06-27
Yes you can. Try this:

dest=/home/folder/lol && export dest

mv file1 $dest && mv file2 $dest

---

### Post by catsails on 2010-06-27
Sometimes it is easier to move multiple files with terminal than drag and drop though. For example, if you have many files with similar names that you want to move. * is a wildcard in terminal, so let's say you're in a music folder and you write mv *.mp3 ~/newdir , it'll move all the mp3 files to that new directory. Or, as a more practical example, yesterday I had to organize results of many model runnings, where the outputs would always have names like l__.ld__.um__.lm__, where the __ are just whatever numbers correspond to that model. So, for all the files corresponding to l71.ld20, I could move them into their own folder with mv l71.ld20.* ~/newdir

If you just want to move files with arbitrary and unrelated names though, I don't know how you'd do that.

---

