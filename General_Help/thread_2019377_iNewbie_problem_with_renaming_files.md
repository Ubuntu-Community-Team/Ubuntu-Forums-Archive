---
title: "iNewbie problem with renaming files"
date: 2012-07-07
forum: General Help
---

### Post by micdac on 2012-07-07
Hi,
I tried to rename files ending with .JPG to .jpg by the following command:

```
mv *.JPG *.jpg
```

and got the following error message:

```
mv: target `*jpg' is not a directory
```


I know there are many solution, I would just like to know why it does not work?

Cheers

---

### Post by codemaniac on 2012-07-07
> **micdac said:**
> Hi,
I tried to rename files ending with .JPG to .jpg by the following command:

```
mv *.JPG *.jpg
```

and got the following error message:

```
mv: target `*jpg' is not a directory
```


I know there are many solution, I would just like to know why it does not work?

Cheers

to understand what your first try says, and why it can't work ,

Suppose you are in a directory containing files 1.JPG , 2.JPG .... n.JPG.
when you fire ```
mv *.JPG *.jpg
```

it gets expanded to 
```
mv 1.JPG 2.JPG .. *.JPG
```

Your shell performed wildcard expansion (also known as globbing).


you can script like below .
```

for filename in *.JPG
do
        file=`basename "$filename" .JPG`
        mv "$filename" "$file".jpg
done

```

---

### Post by steeldriver on 2012-07-07
... or you could use the perl-based 'rename' command,

```
rename -v 's/.JPG/.jpg/' *.JPG
```The -v for verbose is optional, you might want to remove it if you have 1000's of files; you can add -n to do a dry-run without actually renaming:

```
rename -nv 's/.JPG/.jpg/' *.JPG
```

---

