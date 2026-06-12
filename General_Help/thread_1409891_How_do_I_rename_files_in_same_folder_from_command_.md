---
title: "How do I rename files in same folder from command line?"
date: 2010-02-18
forum: General Help
---

### Post by Ascenti0n on 2010-02-18
I need some quick help. I've just spent 20 mins trying to do something I could have done manually in 5, but I think it would be good to know rather than give up.

I want to rename files in the same directory from .html to .php

In the bash terminal I entered:
mv *.html *.php

That didn't work, so I looked at the man page and saw the -T option for same directory, so I entered:
mv -T *.html *.php

still having problems renaming.

Can anyone tell me where I'm going wrong and give proper command?

---

### Post by Barrucadu on 2010-02-18
The rename command is what you need:

```
rename .html .php *.html
```

---

### Post by Ascenti0n on 2010-02-18
that didn't work. Return was: syntax error at (eval 1)

---

### Post by sisco311 on 2010-02-18
On Debian based systems rename is a perl script. 

```
rename 's/.html$/.php/' *.html
```

---

### Post by KeLa on 2010-02-18
You can also try this:
```
find . -type f -name "*.html" -exec rename -v 's/\.html/\.php/' {} \;
```It will rename those html files recursively from all subdirectories also.

---

### Post by sisco311 on 2010-02-18
This should work in most distros:
```
for file in *.html; do 
  mv -b "${file}" "${file%.html}.php"
done
```


or
```
find ./ -type f -name "*.html" | \
while read file; do 
  mv -b "${file}" "${file%.html}.php"
done
```to rename the files recursively.

---

### Post by Ascenti0n on 2010-02-18
> **sisco311 said:**
> On Debian based systems rename is a perl script. 

```
rename 's/.html$/.php/' *.html
```

Thanks, the above worked, but why is the command so complicated and why am I forced to have to use something based on Pearl?

And why doesn't the simple: mv -T *.html *.php work?

Grrrrrrrrrrr

---

### Post by DaithiF on 2010-02-18
> **Ascenti0n said:**
> Thanks, the above worked, but why is the command so complicated and why am I forced to have to use something based on Pearl?

It is no more complicated than it needs to be.  You are not forced to use anything, and its Perl, not Pearl.

> 
And why doesn't the simple: mv -T *.html *.php work?

Grrrrrrrrrrr

how could this work?  lets see what happens with this command:
1. Shell expansion will result in the wildcard '*' characters being expanded, if possible.
So *.html will become file1.html file2.html etc.... depending on whatever html files are in that directory. 
*.php will try to expand into whatever php files are in the directory, but since there aren't any (yet!), the expansion fails, and the shell just leaves it as *.php.  So the command (after shell expansion) looks like:
mv -T file1.html file2.html file3.html *.php
2. Now this command gets executed, ie. mv is called with this parameter list ... how do you expect mv to know that that the parameters file1.html file2.html file3.html *.php means "rename this list of files except the last, changing the suffix of each to the suffix of the last entry in the list?"

---

