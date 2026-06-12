---
title: "How to do this in bash?"
date: 2010-04-14
forum: General Help
---

### Post by RobertL on 2010-04-14
I have a bunch of files with names in the form bb4XXXXXXX.py where the XXXXXXX varies from file to file and is not always the same length. How can I change all the file names to bb5XXXXXXX.py without retyping each one? IOW for each file I want to change the 4 to a 5 while keeping the other characters in the file name unchanged. I imagine there is a way to use for ... do... done with some magic metacharacters to get the job done but I haven't been able to find the magic.

---

### Post by nothingspecial on 2010-04-14
A combination of find with sed or awk.
```

man find
man sed
man awk
```

---

### Post by aeiah on 2010-04-14
if all files start with bb4 and you want them to start with bb5, this is a lot simpler than 'replacing the first instance of 4 with 5', if you know what i mean.

i dont know the syntax of the top of my head but you should be able to search for 'bash filename find and replace'.

or you could have a look at [my batch renamer]("http://aeiah.blogspot.com/2010/04/batch-renamer-using-python-string.html"). its not bash though, its python. it lets you use python string methods on a bunch of filenames all at once.

if you were to use it in this instance, you'd use this syntax:
```

n.replace('bb4','bb5')

```

---

### Post by gzarkadas on 2010-04-14
Try this:

```
for file in bb4*.py do mv ${file} "bb5${file:3}" ; done
```If you want to make sure, before commiting, try:

```
for file in bb4*.py do echo "bb5${file:3}" ; done
```This will be your friend, especially section 3.5 "Shell Expansions", subsection "Shell Parameter Expansion":

```
info bash
```

---

### Post by kaibob on 2010-04-14
Another way to do what you want:

```
rename -n 's/^bb4/bb5/' *
```

The -n option directs rename to do a dry run and report proposed changes. Substitute -v for -n to actually rename the files.

---

### Post by RobertL on 2010-04-14
> **gzarkadas said:**
> Try this:

```
for file in bb4*.py do mv ${file} "bb5${file:3}" ; done

```

gzarkadas' answer is what I was looking for. I expected something like that but I couldn't find the exact syntax. Thanks. (Except that it needs a semicolon before "do".)

But kaibob's suggestion actually seems best. I wasn't aware of the 'rename' command until now. It seems pretty specialized but it does this job very nicely. Thanks kaibob.

---

### Post by kaibob on 2010-04-14
I'm glad that helped. If you ever have the need to use the rename command again, have a look at the following forum post by sisco311. It has a lot of useful examples.

[http://ubuntuforums.org/showpost.php?p=5210607&postcount=2](http://ubuntuforums.org/showpost.php?p=5210607&postcount=2)

---

### Post by roscoecojn on 2011-01-11
> **RobertL said:**
> I have a bunch of files with names in the form bb4XXXXXXX.py where the XXXXXXX varies from file to file and is not always the same length. How can I change all the file names to bb5XXXXXXX.py without retyping each one? IOW for each file I want to [[COLOR=#000000]change[/COLOR]](http://www.********.com/es/software/why-are-ebooks-growing-so-rapidly.html) the 4 to a 5 while keeping the other characters in the file name unchanged. I imagine there is a way to use for ... do... done with some magic metacharacters to get the job done but I haven't been able to find the magic.Thanks for your analysis! This is what I'm looking for, I understand this part.

---

