---
title: "Bash file wildcard problem"
date: 2011-07-06
forum: General Help
---

### Post by jacoder on 2011-07-06
I'm trying to write a script for processing some ogg files, but I can't get the asterisk wildcard to behave like I want it to.  Here is the code:

```

for f in 100*.ogg; do
    ...
    echo $f
    ...
    #code to process file here
done

```the output shows just one entry of "100*.ogg" as a literal file.  Now if I modify it and change the wildcard to 10*.ogg, 1*.ogg, or simply *.ogg, it works with no problem (but there are 300 ogg files on disk and I want to filter for testing).  I tried putting quotes around the mask, but this reads all masks as literal.  I tried to expand to 100nnn-name-*.ogg, which did work as long as there are some alphabetic characters before the asterisk.  There are files in the folder that matches the 100*.ogg mask.  I have noticed bash reads the mask as a literal if no files with that mask exist, but this is not the case.  

I tried Googling this, but it's hard to search for anything involving an asterisk mask.  Why does three or more digits leading into an asterisk produce literals, but a mixed alphanumeric lead and a 2-digit lead (or less) read the mask properly?

Edit: I tried 101*.ogg, and it works, but 100*.ogg produces a literal.  So evidently it's only 100.  Strange.

---

### Post by jacoder on 2011-07-06
Okay, I just realized the problem.  the 100*.ogg files were all given a OGG (uppercase) extension, and the searcher must have not recognized it.  Which brings up another question.  How do you case-insensitive file for  loops?

---

### Post by nothingspecial on 2011-07-06
Probably a better way but

```
for f in 100*.{ogg,OGG}; do echo "$f"; done
```

---

### Post by sisco311 on 2011-07-06
*.[oO][gG][gG] or in bash you can use the nocaseglob option. nullglob is also useful in scripts.

See:
```

man bash | less +/" +shopt \[

```

---

