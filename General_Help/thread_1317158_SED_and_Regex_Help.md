---
title: "SED and Regex Help"
date: 2009-11-06
forum: General Help
---

### Post by prem1er on 2009-11-06
I need to change the delimitation of a file from a number of spaces to | delimitation. Here is an example of one line of the file. How would I replace all the spaces between each field with one | character?  Thanks.  

```
55010647504000       7504000              ATX
```

---

### Post by benj1 on 2009-11-06
```
sed -e 's/  */|/g' -e 's/_-_/-/g'
```

or to do it in bulk

```
for file in *; do mv "$file" `echo $file | sed -e 's/  */|/g' -e 's/_-_/-/g'`; done
```

---

### Post by prem1er on 2009-11-06
Thanks. What is this part doing?

```
-e 's/_-_/-/g'
```

---

### Post by alphaniner on 2009-11-06
And why the '-e'?  The man page is not helping me understand.  I do the same basic thing with just ```
sed 's/  */ /g'
``` in a script to turn multiple spaces into one space, and it hasn't let me down.

---

### Post by falconindy on 2009-11-06
> **benj1 said:**
> ```
sed -e 's/  */|/g' -e 's/_-_/-/g'
```

or to do it in bulk

```
for file in *; do mv "$file" `echo $file | sed -e 's/  */|/g' -e 's/_-_/-/g'`; done
```
Your second "bulk" rename will break horribly as Bash happily splits filenames on white spaces, unless you redefine the IFS. You need to use a structure such as:
```
ls | while read file;do
  mv "$file" `echo $file | sed -e 's/ */|/g'`
done
```
The 'read' program will split on EOL characters.

---

### Post by benj1 on 2009-11-06
> **alphaniner said:**
> And why the '-e'?  The man page is not helping me understand.  I do the same basic thing with just ```
sed 's/  */ /g'
``` in a script to turn multiple spaces into one space, and it hasn't let me down.

hmmm youre right, it was part of a script i had stashed away, im not a big sed person, can't even remember is i wrote it.  


@falconindy
ive never had the problem personally, but noted

---

### Post by bodhi.zazen on 2009-11-06
> **alphaniner said:**
> And why the '-e'?  The man page is not helping me understand.  I do the same basic thing with just ```
sed 's/  */ /g'
``` in a script to turn multiple spaces into one space, and it hasn't let me down.

> **benj1 said:**
> hmmm youre right, it was part of a script i had stashed away, im not a big sed person, can't even remember is i wrote it.  


@falconindy
ive never had the problem personally, but noted

Here is a fun little article on sed 

[http://www.oracle.com/technology/pub/articles/dulaney_sed.html](http://www.oracle.com/technology/pub/articles/dulaney_sed.html)

May be more then you wanted to know =)

---

### Post by benj1 on 2009-11-06
> **bodhi.zazen said:**
> Here is a fun little article on sed 

[http://www.oracle.com/technology/pub/articles/dulaney_sed.html](http://www.oracle.com/technology/pub/articles/dulaney_sed.html)

May be more then you wanted to know =)

thanks

im more of an awk man my self :D

i suppose the simplest would have been 
```
tr " " "|"
```

hindsights a wonderful thing

---

### Post by DaithiF on 2009-11-06
> i suppose the simplest would have been 
 	Code:
 	tr " " "|"

sorry to be pedantic :), but that wouldn't work so well for multiple spaces ... e.g.:
```
echo "one space and then       lots       of     spaces" | tr " " "|"
one|space|and|then|||||||lots|||||||of|||||spaces
```
so you need the -s option for tr to squeeze sequential spaces into just one before replacing with the |, ie.
```
echo "one space and then       lots       of     spaces" | tr -s " " "|"
one|space|and|then|lots|of|spaces
```

---

### Post by benj1 on 2009-11-06
> **DaithiF said:**
> sorry to be pedantic :), but that wouldn't work so well for multiple spaces ... e.g.:
```
echo "one space and then       lots       of     spaces" | tr " " "|"
one|space|and|then|||||||lots|||||||of|||||spaces
```
so you need the -s option for tr to squeeze sequential spaces into just one before replacing with the |, ie.
```
echo "one space and then       lots       of     spaces" | tr -s " " "|"
one|space|and|then|lots|of|spaces
```
thanks

although to be really pedantic

```
tr -s "[:space:]" "|"
```

would be better just in case you like using newlines and tabs in file names ;)

---

### Post by ghostdog74 on 2009-11-09
no need to be so complicated with regex... use awk
```

# awk '{$1=$1}1' OFS="|"  file
55010647504000|7504000|ATX

```

---

