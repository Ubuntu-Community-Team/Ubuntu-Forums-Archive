---
title: "Remove special characters from many file names recursively"
date: 2010-01-18
forum: General Help
---

### Post by moodog on 2010-01-18
I use Linux, and use a back up hard disk to store many, many files in a deep directory structure. Some of these files have characters in them that are legal in Linux, but Windows does not like them. When I share the HD with a friend who only uses Windows, unfortunately he is unable to read a lot of the files. 

Short of convincing him to move to Linux, is there an easy way to rename all of the problematic files to remove the special (illegal in Windows) characters?

---

### Post by KeLa on 2010-01-18
You can try something like this:
```
find ~/test/ -type f -name "*.*" -exec rename -v 's/äöåÄÖÅ/aoaAOA/' {} \;
```
it will search from test directory recursively all files and rename those so that äöå etc are substituted with aoa etc.

---

### Post by moodog on 2010-01-19
Any other suggestions? This only works for one special character at a time, for some reason not all - i.e. :

```
> touch aeiöåÄÖÅ.txt

> find . -type f -name "*.*" -exec rename -v 's/äöåÄÖÅ/aoaAOA/' {} \;
```

no output
even for:

```
> rename -v 's/äöåÄÖÅ/aoaAOA/' aeiöåÄÖÅ.txt
```

however :

```
>  rename -v 's/ö/o/' aeiöåÄÖÅ.txt 
aeiöåÄÖÅ.txt renamed as aeioåÄÖÅ.txt

```

---

### Post by KeLa on 2010-01-19
Ok.

Try to add those charactes to brackets like this

```
s/[öäåÖÄÅ]/[oaoOAO]/
```

---

### Post by john newbuntu on 2010-01-19
Why re-invent the wheel when devarthur has it:
[http://devarthur.blogspot.com/2008/08/copying-files-from-linux-to-windows.html](http://devarthur.blogspot.com/2008/08/copying-files-from-linux-to-windows.html)

---

### Post by alwayshere on 2010-01-19
krename is the best and most easy to use i have founduse below command in terminal to install it. 

sudo apt-get install krename

and to launch it. 

krename

Or theres a launcher under applications / accessories

---

### Post by jamesisin on 2010-01-19
Setting all name changing aside for the moment, if you run a Samba share your friends will be able to access the files but the file names will be altered using some (fantastically retarded) Windows convention.

---

### Post by ztyx on 2012-10-05
> **KeLa said:**
> Ok.

Try to add those charactes to brackets like this

```
s/[öäåÖÄÅ]/[oaoOAO]/
```

This is wrong. You are not fully understanding Perl-style regexp substitutions correctly. Unfortunately, you can't get away with a single rename. Instead you will need to do multiple ones:

```

$ find . -type f -exec rename 's/[åä]/a/g' {} +
$ find . -type f -exec rename 's/[ö]/o/g' {} +
$ find . -type f -exec rename 's/[ÅÄ]/A/g' {} +
$ find . -type f -exec rename 's/[Ö]/O/g' {} +

```

They could be combined using

```

$ find . -type f -exec rename 's/[åä]/a/g' {} + -exec rename 's/[ö]/o/g' {} + -exec rename 's/[ÅÄ]/A/g' {} + -exec rename 's/[Ö]/O/g' {} +

```

If you simply would like to remove all non-alphanumeric characters you could do something like:

```

$ find . -type f -exec rename 's/[^A-Za-z0-9._]//g' {} +

```

---

