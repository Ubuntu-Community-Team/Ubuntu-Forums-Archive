---
title: "rsync -- Do I have to delete ALL the spaces in dirs and/or filenames?"
date: 2012-02-10
forum: General Help
---

### Post by nslegacy163 on 2012-02-10
Hi gang, 

 I'm attempting a rsync using:
```
 sudo rsync -azvu --progress --exclude="/*/.gvfs" -n /media/FileShare/My Documents /media/1TBBACKUP

```

 As expected the command errors out because it cannot find the directory "/media/FileShare/My " because of the space. So while I went in to delete the space I thought to myself, "Self, do I have to delete all the spaces?!" It's a large external HDD that has a few directories in it that utilize the human-readable space directory and file name...please tell me I don't have to delete all the spaces and only the one in the "My Documents" part will suffice. 


Thanks

Drew

---

### Post by forrestcupp on 2012-02-10
No, just use a backslash '\' before each space. So it would look like

/My\ Documents/

---

### Post by nslegacy163 on 2012-02-10
Looks like I figured it out. 

 The answer is, "Self, you only need to delete the space in "My Doc..."

Thanks for the quick response!

---

### Post by nslegacy163 on 2012-02-10
> **forrestcupp said:**
> No, just use a backslash '\' before each space. So it would look like

/My\ Documents/
Yeah, thanks for the that too! I figured it out just as this reply came through.

---

### Post by forrestcupp on 2012-02-11
The backslash '\' is called an escape character. Whenever you need to use any character that is normally not usable, like a space, you precede it with a \ to tell the computer that the space is part of the string. Incidentally, if you ever need a backslash to be part of the name, you would just use two backslashes, "\\". It's used mostly in programming, but it works for filenames here, too.

---

### Post by forrestcupp on 2012-02-12
> **nslegacy163 said:**
> Looks like I figured it out. 

 The answer is, "Self, you only need to delete the space in "My Doc..."

Thanks for the quick response!

The only thing is, if you actually delete the space in "My Documents", when you boot back into Windows, it could screw up anything that referrs to "My Documents" with a space.

---

### Post by papibe on 2012-02-12
forrestcupp's suggestions work great for local files.

When rsyncing from or to a remote host, consider using the option --protect-args to be extra safe.

Just a thought.
Regards.

---

