---
title: "Bash for loop is strange.  Bug?"
date: 2010-05-28
forum: General Help
---

### Post by zoubidoo on 2010-05-28
The bash for loop is confusing me:
```
$ mkdir foo
$ for i in foo/*  ; do echo $i ; done
foo/*
$ 

```
foo is an empty directory - nothing is found, so why return a result?  The loop should iterate zero times.

Surely, this must lead to lots of programming errors.

Zoubidoo

---

### Post by zoubidoo on 2010-05-28
According to the bash reference manual: [http://www.gnu.org/software/bash/manual/bashref.html#Looping-Constructs](http://www.gnu.org/software/bash/manual/bashref.html#Looping-Constructs)

```
for name [ [in [words ...] ] ; ] do commands; done
```
[..] If there are no items in the expansion of words, no commands are executed, and the return status is zero.

So it's not the for loop it's related to filename expansion. [http://www.gnu.org/software/bash/manual/bashref.html#Filename-Expansion](http://www.gnu.org/software/bash/manual/bashref.html#Filename-Expansion)

[..] If no matching file names are found, and the shell option nullglob is disabled, the word is left unchanged.

Do
```
shopt -s nullglob 
```
then no results are returned.  Personally, I'd make this the default.


I just learned something.  Bash, you are strange!

---

### Post by zoubidoo on 2010-05-28
shopt is bash-specific.  So how can the same thing (nullglob) be done in a portable way?

---

### Post by DaithiF on 2010-05-28
> **zoubidoo said:**
> shopt is bash-specific.  So how can the same thing (nullglob) be done in a portable way?
I guess you could do:
```
find foo -mindepth 1 | while read file; do echo "In loop, file is: $file"; done
```

---

### Post by gmargo on 2010-05-28
> **zoubidoo said:**
> shopt is bash-specific.  So how can the same thing (nullglob) be done in a portable way?

One easy way:
```

for i in $(ls foo/* 2>/dev/null) ; do echo $i ; done

```Of course, in the general case, it wouldn't really matter because you'd be testing further:
```

for i in foo/*
do
    if [ -f "$i" ]; then
        echo "$i is a file"
    fi
done

```

---

