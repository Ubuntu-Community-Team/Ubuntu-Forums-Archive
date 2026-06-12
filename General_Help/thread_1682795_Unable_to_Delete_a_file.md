---
title: "Unable to Delete a file"
date: 2011-02-06
forum: General Help
---

### Post by prongsie on 2011-02-06
So, I'm still fairly new to Linux, I really don't know much. My problem is with a file that I can't delete, or move for that matter.

My dad was just randomly saving pictures and deiced he wanted to trash it. I don't know what he did, but in no longer has a file name, just the extension jpeg. Now I tried to right click it and move to the trash, but that option isn't highlighted, same for the rename. When I try to move it, it says the file does not exist. Here is what is says exactly: 

Error stating file '/home/ashley/Desktop/Ed/dads files/TV Shows/isis (joanna cameron)/jpeg': No such file or directory

I would love some help with this. >> Thanks so much!

---

### Post by cjhabs on 2011-02-06
> **prongsie said:**
> So, I'm still fairly new to Linux, I really don't know much. My problem is with a file that I can't delete, or move for that matter.

My dad was just randomly saving pictures and deiced he wanted to trash it. I don't know what he did, but in no longer has a file name, just the extension jpeg. Now I tried to right click it and move to the trash, but that option isn't highlighted, same for the rename. When I try to move it, it says the file does not exist. Here is what is says exactly: 

Error stating file '/home/ashley/Desktop/Ed/dads files/TV Shows/isis (joanna cameron)/jpeg': No such file or directory

I would love some help with this. >> Thanks so much!

You could try removing it from the command line - from a terminal window:
```

cd '/home/ashley/Desktop/Ed/dads files/TV Shows/isis (joanna cameron)'

```
(you need the single close quote around the path to escape the spaces)
```

ls -l

```
(this will list the file - note the filename)
```

rm filename

```
(where filename is the name of the problem file - this should delete it)
If it again doesn't find it, it is probably because there is a strange character in the name, so - carefully try this - again in that folder)
```

rm -i *

```
This will go every file in the folder and ask if you want to delete it - answer 'y' to delete the problem file - 'n' to skip over the other files.

---

