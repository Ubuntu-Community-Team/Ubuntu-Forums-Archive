---
title: "Conky help?"
date: 2011-01-31
forum: General Help
---

### Post by IceGuru on 2011-01-31
[http://ubuntuforums.org/showpost.php?p=10184645&postcount=14986](http://ubuntuforums.org/showpost.php?p=10184645&postcount=14986)

I really love that conky config.

But I can't figure out how to set up the files instead the archive. Can someone help me?

---

### Post by stinkeye on 2011-01-31
Extract the archive to your home folder.
Rename the folder **CrinosConky** to **.conky** (include the preceeding dot.)

Now if you show hidden files and open your **~/.conky** folder
you will see the **.conkyrc** config.

You can start conky using your **~/.conky/.conkyrc** config with
```
conky -c ~/.conky/.conkyrc
```


If you want to load this config by just entering "**conky**" in the terminal,
you will need to move the **~/.conky/.conkyrc** file into your home directory.

I get a lot of errors when running so you will need to do edit the files
in the conkyparts folder to suit your setup.

He is using a lot of scripts and this may not be the best config if your just
starting to use conky.

---

