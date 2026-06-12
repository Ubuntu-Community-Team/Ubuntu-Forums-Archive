---
title: "Find all executable text files on my PC?"
date: 2012-06-22
forum: General Help
---

### Post by Rytron on 2012-06-22
Hi.

How could I find all executable text files in ~/Documents and all sub-directories on mu PC?

I want to make them non-executable.

Thanks.

---

### Post by SlugSlug on 2012-06-22
> **Rytron said:**
> Hi.

How could I find all executable text files in ~/Documents and all sub-directories on mu PC?

I want to make them non-executable.

Thanks.


cd to Documents 

for i in `ls *.txt -R` ; do chmod 660  $i ; done

---

### Post by Rytron on 2012-06-22
> **SlugSlug said:**
> cd to Documents 

for i in `ls *.txt -R` ; do chmod 660  $i ; done

Thanks but how would I actually find the ones that are executable? I should explain that I copied many files (contained a good few text file sym links) from my laptop to my desktop (both GNU/Linux). Instead of copying the sym links as links it copied them as executable text files. Thus, if I can locate all the executable text files, I can delete them and make new sym links.

---

### Post by nothingspecial on 2012-06-22
```
find ~/Documents -executable -type f
```

---

### Post by Rytron on 2012-06-22
> **nothingspecial said:**
> ```
find ~/Documents -executable -type f
```

And getting it to only show executable text files?

---

### Post by nothingspecial on 2012-06-22
```
find ~/Documents -name "*.txt" -executable -type f
```

---

### Post by Rytron on 2012-06-22
> **nothingspecial said:**
> ```
find ~/Documents -name "*.txt" -executable -type f
```

Nice one!

---

### Post by kimda on 2012-06-22
Find all files beneath current directory and strip executable from user,group and other.
```
find . -type f -print0 | xargs -0 chmod ugo-x
```

Of you could use this command to change rw to user and group and r to other for all files (common). 
```
find . -type f -print0 | xargs -0 chmod 664
```

---

### Post by Rytron on 2012-06-22
> **kimda said:**
> Find all files beneath current directory and strip executable from user,group and other.
```
find . -type f -print0 | xargs -0 chmod ugo-x
```

Of you could use this command to change rw to user and group and r to other for all files (common). 
```
find . -type f -print0 | xargs -0 chmod 664
```

Hi kimda. How could you amend it to remove all executable permissions from only text files?

---

### Post by CharlesA on 2012-06-22
> **Rytron said:**
> Hi kimda. How could you amend it to remove all executable permissions from only text files?
Easy:

```
find ~/Documents -name "*.txt" -executable -type f -exec chmod -x {} \;
```

You might want to check here too: [http://ubuntuforums.org/showthread.php?t=1288103](http://ubuntuforums.org/showthread.php?t=1288103)

That one will remove execute from all files.

---

### Post by Rytron on 2012-06-22
Thank you guys. ;)

---

