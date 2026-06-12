---
title: "Quick locate/updatedb question"
date: 2010-05-23
forum: General Help
---

### Post by lariosa42 on 2010-05-23
Can "locate" or "updatedb" be set to print file names with white space properly escaped?  For example, I want it to print, "/home/USER/My\ Files" and not, "/home/USER/My Files".  

I've googled around, read the man pages, checked the forum, and I'm still stuck.  Any help would be appreciated.

---

### Post by happyhamster on 2010-05-23
```

user@pc:~$ locate happyhamster
/home/user/Test folder name/happyhamster

```

```

user@pc:~$ locate happyhamster | sed 's/\ /\\ /g'
/home/user/Test\ folder\ name/happyhamster

```

```

's'   = search for
'\ '  = a space character,
'\\ ' = replace with a slash and a space
'g'   = do this for all spaces found

```

---

### Post by lariosa42 on 2010-05-23
Thanks, I should have thought of that.  It's not quite as quick and automated as I would like (it would be nice to be able to make updatedb write the file names exactly as they occur when you need to pipe them somewhere), but this will definitely save me some trouble.  Thanks again!

---

