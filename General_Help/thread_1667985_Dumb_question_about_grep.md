---
title: "Dumb question about grep"
date: 2011-01-15
forum: General Help
---

### Post by GuiGuy on 2011-01-15
I want list files of a particular type and I need to do that recursively. So I do

ls -R | grep .avi

thinking it might give me all the files with .avi extensions. However, it also returns every other file with "avi" in it, like "n**avi**gator". So it seems the dot is being ignored or has another meaning to grep.

How would I go about listing only those files that have a .avi extension?

TIA

---

### Post by abdulapopoola on 2011-01-15
Try this:
ls -R | grep *.avi
Should do the trick.
Have fun. ;)

---

### Post by sisco311 on 2011-01-15
The period . matches any single character. You have to escape it:
```
ls -R | grep \.avi$
```

See:
```
man grep | less +/"REGULAR EXPRESSIONS"
```

---

### Post by Smart Viking on 2011-01-15
Yes that is correct, it has another meaning.

```
ls -R | grep "\.avi"
```
By putting a "\" infront of it, it will match ".". :)

---

### Post by dental on 2011-01-15
If you're searching for files by file name/extension then find is a better tool. In this case:

```
find . -name \*.avi
```would do the trick.

For more fun, man find. :) It's got a host of options.

---

### Post by GuiGuy on 2011-01-15
> **abdulapopoola said:**
> Try this:
ls -R | grep *.avi
Should do the trick.
Have fun. ;)

No, I don't think the wild card trick works. It returns nothing for me.

---

### Post by GuiGuy on 2011-01-15
> **Smart Viking said:**
> Yes that is correct, it has another meaning.

```
ls -R | grep "\.avi"
```
By putting a "\" infront of it, it will match ".". :)

That's the one!

Thanks.

---

### Post by GuiGuy on 2011-01-15
Thanks for the help, people. 

Cheers

---

