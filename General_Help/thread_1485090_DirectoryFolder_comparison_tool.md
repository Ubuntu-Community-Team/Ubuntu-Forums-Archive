---
title: "Directory/Folder comparison tool"
date: 2010-05-16
forum: General Help
---

### Post by siddartha on 2010-05-16
I'm having a large directory with quite a few subdirectories filled with photos. On a second system I have about the same in a different sort. There is also a backup on external media.

Now I have the need to sort all of this and decide which directories/folders have to go and which to merge. Is there a tool that can do such a comparison in the GPL world?

PS: all I find is diff tools for CVS. I know Ubuntu is a geek system, but maybe there are tools that work with photos as well.

---

### Post by abcuser on 2010-05-16
This can probably be done in several ways.

Try this out. Open Terminal and on first path you would like to search execute command (the command will write to file first_path.txt all the directories/subdirectories from current directory):
```
ls -R | gawk 'substr($1,1,1)=="." {print}' | sort -u > first_path.txt
```

Then on the second path do the same except name file e.g. second_path.txt (the command will write to file second_path.txt all the directories/subdirectories from current directory):
```
ls -R | gawk 'substr($1,1,1)=="." {print}' | sort -u > second_path.txt
```

Then compare the two files:
```
comm -23 first_path.txt second_path.txt
```

and vice versa compare:
```
comm -13 first_path.txt second_path.txt
```

Comm command will display you all the directories that are listed on first and are not available in second list of directories and vice versa for second comm command.

I know this is little bit geeky answer, but I can't think of anything simpler.

---

### Post by davec64 on 2010-05-16
Gnome Commander has a comparison option between the two panes if you want to do it the GUI way. :)

---

