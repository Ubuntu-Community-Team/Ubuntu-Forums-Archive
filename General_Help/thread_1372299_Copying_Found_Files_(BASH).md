---
title: "Copying Found Files (BASH)"
date: 2010-01-04
forum: General Help
---

### Post by Chamillionaire2 on 2010-01-04
What's Up?

OK, So I'm trying to copy files that the terminal command "find" finds. So for example.
```
find . -name "*.js"
```
Will find me " ./folder/js.js " But how do I then get it to then copy the found file(s) to another dir?

Thanks Bye!

---

### Post by junapp on 2010-01-04
something like this:
```

find ./ -name "*.js" -exec cp {} /some/other/path \; 

```edit:
some similar other options discussed at:
[http://ubuntuforums.org/archive/index.php/t-405261.html](http://ubuntuforums.org/archive/index.php/t-405261.html)

edit 2: Caution
might want to read through the 'man find' page for some warnings on using the -exec action.

---

### Post by Chamillionaire2 on 2010-01-04
> **junapp said:**
> something like this:
```

find ./ -name "*.js" -exec cp {} /some/other/path \; 

```edit:
some similar other options discussed at:
[http://ubuntuforums.org/archive/index.php/t-405261.html](http://ubuntuforums.org/archive/index.php/t-405261.html)

edit 2: Caution
might want to read through the 'man find' page for some warnings on using the -exec action.

Terminal Wizard lol, Thanks Alot :-)

---

