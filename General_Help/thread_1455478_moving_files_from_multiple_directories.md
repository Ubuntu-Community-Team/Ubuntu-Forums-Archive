---
title: "moving files from multiple directories"
date: 2010-04-16
forum: General Help
---

### Post by Velvet Karuda Leopard on 2010-04-16
Ok.  I have a directory tree with lots of folders.  I need to gather all files of same type, say .txt, and place them in a different folder all by themselves.

I know I can use the mv command, but it won't let me go through all the subdirectories of my folder, just the current one.

How can I search through all subdirectories for all .txts or whatever and move them to a folder of my choosing?

---

### Post by noremacyug on 2010-04-16
not sure what version you are running, but in 10.04 i tried to see if i could do what i think you are wanting to accomplish.

for me i decided to search my home directory for any .txt files.

i simply went to my "home" directory in nautilus and clicked on the "go" button at the top, then selected "search for files" from the drop down list.  it then added a search toolbar to nautilus.  i put .txt in the box and clicked search, it then brought up every text file it found in all the sub directories of my "home" directory.  you can then select, copy, move, delete whatever you want.

hopefully this helps, unless i've misunderstood what you are trying to do.

---

### Post by nothingspecial on 2010-04-16
You need to use find

For this example I`m going to assume that all the .txt files are located in directories and subdirectories of your Documents folder and you want to move them to a directory in your home called scripts
```

find ~/Documents -name '*.txt' -exec mv '{}' ~/scripts \;
```

---

