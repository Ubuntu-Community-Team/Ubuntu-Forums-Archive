---
title: "using cp to copy files"
date: 2010-11-18
forum: General Help
---

### Post by Drenriza on 2010-11-18
I have a folder that contains multiple files i want to copy.

file1_DK, file2_DK, file3_DK, file4_NO

If i wanted to copy files1-3_DK but exclude file4_NO how would i do that?

Thanks on advance.
Kind regards

---

### Post by stefangr1 on 2010-11-18
If the files have something unique, it's simple:

```
cp *DK /destination/
```

This means copy everything that ends on "DK". If there's nothing unique in the filenames of files you wan't to copy or not to copy, you have to write a simple shell script. A simple shell script that would do it would look like this:

```
#!/bin/sh

for ((x = 1; x <= 3; x++))
do
        if [ -f "file${x}_DK" ];
        then
                cp "file${x}_DK" /destination/
        fi
done

exit 0
```

---

### Post by Drenriza on 2010-11-18
how would i do the following using this
```

#!/bin/sh

for ((x = 1; x <= 3; x++))
do
        if [ -f "file${x}_DK" ];
        then
                cp "file${x}_DK" /destination/
        fi
done

exit 0
```i want to copy
dog, cat, train, bird, ice

but exclude 
car, rocket and mijaw

---

### Post by stefangr1 on 2010-11-18
I'll stick to the country example. Let's assume you want to copy files 1 to 3 for Denmark and Luxembourg (and not for any other countries). This is done as follows:

```
#!/bin/sh

for name in DK LU
do
        for ((x = 1; x <= 3; x++))
        do
                if [ -f "file${x}${name}" ];
                then
                        cp "file${x}${name}" /destination/
                fi
        done
done

exit 0
```

---

### Post by Drenriza on 2010-11-18
and thats cool. But im not the big programmer here, so maybe its obvious to others and not me. But can i use this to do copy the word thing, where the files does not have something in commen?

---

### Post by CharlesA on 2010-11-18
Is this homework?

---

### Post by sisco311 on 2010-11-18
> **Drenriza said:**
> 
i want to copy
dog, cat, train, bird, ice

but exclude 
car, rocket and mijaw



```
man bash | less +/"\!\(pattern-list\)"
```

---

### Post by Drenriza on 2010-11-19
> **CharlesA said:**
> Is this homework?

Hehe, i cant say that it is ,) my school is not advanced enough to teach in unix / linux systems.

But seriously, it is work related.

---

### Post by sisco311 on 2010-11-19
> **Drenriza said:**
> Hehe, i cant say that it is ,) my school is not advanced enough to teach in unix / linux systems.

But seriously, it is work related.

I guess, you didn't figured out how !(pattern) works.

In case you want to copy anything from a directory but the files *car, rocket and mijaw*, you have to run something like:
```
cp !(car|rocket|mijaw) path/to/dir
```

---

### Post by Drenriza on 2010-11-19
sry sisco311 the
```
man bash | less +/"\!\(pattern-list\)"
```Is in my opinion brilliant. But i just havnt had the time today to read it.

But thanks!
```
cp !(car|rocket|mijaw) path/to/dir
```I must try it out :)

EDIT.
Hehe just tested it out. And from what i can see. The command dosent copy what you type in. What you type in is what you want to exclude.
And then you copy everything else.

---

### Post by CharlesA on 2010-11-19
Yeah. That's the point of having the "!" in front of the pattern.

---

### Post by alphaamanitin on 2010-11-19
> **sisco311 said:**
> I guess, you didn't figured out how !(pattern) works.

In case you want to copy anything from a directory but the files *car, rocket and mijaw*, you have to run something like:
```
cp !(car|rocket|mijaw) path/to/dir
```

+1

This is Fing great.  I had not idea the cp command could be deployed so powerfully.

AlphaA

---

### Post by karthick87 on 2010-11-19
> **Drenriza said:**
> I have a folder that contains multiple files i want to copy.

file1_DK, file2_DK, file3_DK, file4_NO

If i wanted to copy files1-3_DK but exclude file4_NO how would i do that?

Thanks on advance.
Kind regards

```
cp file[123]_DK dst/
```or

```
cp !(file4_NO) dst/
```

---

### Post by Drenriza on 2010-11-22
Thanks all for the help :)

---

### Post by ToFue on 2010-12-03
I believe what you're looking for may be: 

```


$ cp /dir/prefix/{file-a.1,file-b.2,file-c.3} /dest/folder/


```

note that commas separate the sequential file list, enclosed in braces, which encapsulate a particular grouping..

---

