---
title: "Getting Grep to Pull Info from a specifc file wich match all the words"
date: 2011-06-02
forum: General Help
---

### Post by kevinhobson2000 on 2011-06-02
Hi,

I am trying to use grep to only tell me files that include both words matching in a pattern file.  However when i specify:

grep -f <pattern file> <file>


It pulls out anything that matches one or the other.

Not both.

Does anyone know how to get it to match AND not OR.

Cheers

Kev

---

### Post by Habitual on 2011-06-02
drop the "-f" unless -f <file> has the pattern you are searching for.
 
grep <pattern> file

-f FILE, --file=FILE
Obtain  patterns ***from***  FILE, one per line.  
The empty file contains zero patterns, and therefore matches nothing.

[http://unixhelp.ed.ac.uk/CGI/man-cgi?grep](http://unixhelp.ed.ac.uk/CGI/man-cgi?grep)

---

### Post by towheedm on 2011-06-02
To match more than one word you must use extended regex.  For instance to match word1 AND word2:
```
grep -E "(word1&word2)"
```

or to watch either word1 OR word 2:
```
grep -E "(word1|word2)"
```

---

### Post by kevinhobson2000 on 2011-06-02
Hi,

The grep -E.

Didnt pull out anything.

When i specify two words.

Cheers

Kev

---

### Post by DaithiF on 2011-06-02
> **towheedm said:**
> To match more than one word you must use extended regex.  For instance to match word1 AND word2:
```
grep -E "(word1&word2)"
```
or to watch either word1 OR word 2:
```
grep -E "(word1|word2)"
```

No this won't work for the AND case, (though the OR case does work fine).

AND'ing requires a second pass using xargs:

```
grep -l pattern1 * | xargs -I % grep -l pattern2 %
```

so the first grep produces a list of files which match pattern 2, the second grep search those files for the second pattern.

---

### Post by DaithiF on 2011-06-02
just to add, -E "(word1&word2)" matches the literal pattern word1&word2, ie. '&' does not have a special 'AND' meaning within a grep regex.

---

### Post by kevinhobson2000 on 2011-06-02
Dalith,

Top man this seems to be doing what i want.

Thanks

Kev

---

### Post by kevinhobson2000 on 2011-06-02
Dalith,

Can i just check my syntax is correct for this command.  I have:

grep -l "Cust: FI699" gm* | xargs -I % grep -l BACKUP %

Regards

Kev

---

### Post by DaithiF on 2011-06-02
> **kevinhobson2000 said:**
> Dalith,

Can i just check my syntax is correct for this command.  I have:

grep -l "Cust: FI699" gm* | xargs -I % grep -l BACKUP %

Regards

Kev
yep looks fine to me.

---

### Post by kevinhobson2000 on 2011-06-02
Dalith,

One final question:

I have two files one has .new on the end.

Is there anyway i can exclude the .new from the grep.

Thanks

Kev

---

### Post by DaithiF on 2011-06-02
> **kevinhobson2000 said:**
> Dalith,

One final question:

I have two files one has .new on the end.

Is there anyway i can exclude the .new from the grep.

Thanks

Kev

if you've only two files and you want to exclude one ... well just explictly use the name of the other one!!

or if you have lots of gm* files and want to exclude the ones ending with .new, then there are (at least) a couple of ways:

1. using grep's --exclude option:
```
grep --exclude="*.new" -l pattern gm*
```
2. using bash's extglob pattern expansion
first turn on extglob using shopt:
```
shopt -s extglob
grep -l pattern gm!(*.new)

```

---

