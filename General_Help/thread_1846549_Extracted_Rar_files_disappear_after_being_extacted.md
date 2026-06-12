---
title: "Extracted Rar files disappear after being extacted - Ubuntu Natty"
date: 2011-09-19
forum: General Help
---

### Post by AlexOnVinyl on 2011-09-19
For some reason, sometimes, when I extract rar files the files that I unrar disappear... is there anything behind this?

Please assist.

yes I do have unrar and rar installed via package manager.

---

### Post by sisco311 on 2011-09-19
Try to extract the file using the terminal:
```

cd path/to/dir
unrar e file.rar

```

And see if unrar returns any error message.

---

### Post by AlexOnVinyl on 2011-09-19
> **sisco311 said:**
> Try to extract the file using the terminal:
```

cd path/to/dir
unrar e file.rar

```And see if unrar returns any error message.

Actually the unrar command didnt really work... so I used the 7zip-rar syntax
and it worked :D

I posted a tutorial about it for those other people having the same issue:

[http://ubuntuforums.org/showthread.php?p=11265396#post11265396](http://ubuntuforums.org/showthread.php?p=11265396#post11265396)

---

