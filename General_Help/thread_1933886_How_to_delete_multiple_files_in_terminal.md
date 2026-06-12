---
title: "How to delete multiple files in terminal?"
date: 2012-03-01
forum: General Help
---

### Post by Vigh on 2012-03-01
How do I delete multiple files in terminal, there are about 40,000. All start with the word newton, anyway I can simply delete all of these files without deleting anything else contained in the folder.

Regards
Ant.

---

### Post by surfer on 2012-03-01
check out the bash wildcards. and test with ls before removing!

```
$ ls newton*
```
to check and
```
$ \rm newton*
```
to really remove.

---

### Post by nothingspecial on 2012-03-01
You would use a glob.

* is a special character that means any character occurring 0 or more times

```
nothingspecial:~$ ls
86         examples.desktop  playlists                              Templates
Desktop    images            Public                                 Ubuntu One
Distros    Music             Purchased from Ubuntu One              Videos
Documents  Photos            Screenshot at 2012-02-15 07:46:33.png
Downloads  Pictures          source
nothingspecial:~$ echo D*
Desktop Distros Documents Downloads
nothingspecial:~$ 
```

So ```
echo newton*
```

will output all files that begin with those 6 characters. If you are sure they are the ones you want to delete, you can type

```
rm newton*
```

But you might be better moving them all to a folder first to be sure

```
mkdir deleted
mv newton* deleted
```

Then you can delete the folder "deleted"

---

### Post by Vigh on 2012-03-01
rm newton*
bash: /bin/rm: Argument list too long

mv newton* deleted
bash: /bin/mv: Argument list too long

any ideas

---

### Post by Vaphell on 2012-03-01
names of files don't fit in input buffer of rm, that's quite a few names :)

you can go around this issue by using find command

```
find . -maxdepth 1 -iname 'newton*' -exec rm "{}" \;
find . -maxdepth 1 -iname 'newton*' -exec mv "{}" <dest_dir> \;

```
it will look for matching stuff at current level (find is recursive by default) and process one by one with command after -exec switch. {} is a placeholder for the name of objects found.

---

### Post by Khayyam on 2012-03-01
... or similarly (using find) without having to 'exec rm' and provide termination:

```
find . -maxdepth 1 -name "newton*" -delete
```best ... khay

---

### Post by kevdog on 2012-03-01
Seriously -- how did you generate all those files with the name of newton?

---

### Post by Khayyam on 2012-03-01
> **kevdog said:**
> Seriously -- how did you generate all those files with the name of newton?

It's the "[universal law of gravitation](http://en.wikipedia.org/wiki/Newton%27s_law_of_universal_gravitation)" at work .. mass attraction! ... hehe

best ... khay

---

### Post by Vaphell on 2012-03-01
> **Khayyam said:**
> ... or similarly (using find) without having to 'exec rm' and provide termination:

```
find . -maxdepth 1 -name "newton*" -delete
```best ... khay

yup, i always forget about that one ;)

---

### Post by Vigh on 2012-03-01
Making a newtonian based fractal and rendering it in Xaos. Thanks for the help. Regards

Ant.

---

