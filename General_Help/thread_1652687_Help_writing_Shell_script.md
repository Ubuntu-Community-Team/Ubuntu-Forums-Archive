---
title: "Help writing Shell script"
date: 2010-12-25
forum: General Help
---

### Post by U2XS on 2010-12-25
I've read the documentation but can't figure it out.  Let's say that I want to write a shell script which will rename every .jpg file in a folder to prepend "Linux_" to it.
 
Challenge #1: how do I create a loop which is contingent on the amount of files in that folder

Challenge #2: how do I know that file's respective name?

I think it should look like this:

Loop /home/administrator/Images/*.jpg
   (
   Mv THATFILENAME Linux_THATFILENAME
   )

Can this be done?

---

### Post by sisco311 on 2010-12-25
Check out: [http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Loops_.28while.2C_until_and_for.29](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Loops_.28while.2C_until_and_for.29)

```

cd /home/administrator/Images/

for file in *.jpg; do
  mv -b "$file" "Linux_$file"
done

```

---

### Post by WorMzy on 2010-12-25
Assuming you're using bash as your shell, a simple example of a loop involving files would be:
```
for *file* in `ls`
do
echo $*file*
done
```

In this example "*file*" is the name of the variable we give to each file name printed by the ls command (which is executed separately, due to the presence of backticks (`)), you could use anything as it's name, it doesn't have to be file:

```
for *elephant* in `ls`
do
echo $*elephant*
done
```

Also, the backtick'd command and action command (the part after "do") can be more complex, e.g.

```
for file in `ls | grep C`
do
echo "$file hello"
done
```

In your case, I suggest running
```
mv $file "Linux_$file"
```
as the action.

---

### Post by sisco311 on 2010-12-25
> **WorMzy said:**
> Assuming you're using bash as your shell, a simple example of a loop involving files would be:
```
for *file* in `ls`
do
echo $*file*
done
```


Hmmm, a very common mistake... This will fail with files with spaces in their name.

Please check out the link I posted.

---

### Post by WorMzy on 2010-12-25
> **sisco311 said:**
> Hmmm, a very common mistake... This will fail with files with spaces in their name.

Please check out the link I posted.

Ah. Thanks for that, I already liked globs, but now I know that they are my friends. :P

---

### Post by U2XS on 2010-12-25
Thanks guys. I wound up going with the first solution & it works like a charm.

---

### Post by U2XS on 2010-12-25
In reality, I needed this code to process images into several sub folders (rather than renaming files).  I got it working exactly as I want it.  However I can't seem to get it to work with the FTP command.  Does this mean I need to log in and out for every iteration that it has to upload?

I am using this code.

```
#!/bin/bash

filename="/home/paul/myfile.tar.gz"
hostname="ftp.myhost.com"
username="username"
password="password"
ftp -un $hostname <<EOF
quote USER $username
quote PASS $password

binary
put $filename
quit
EOF
```

---

### Post by U2XS on 2010-12-26
Last question!

I would like the for loop to affect the .jpg as well as the .JPG files.  I tried, this, but it didn't work

```
for file in *.jpg || *.JPG; do 
echo Either .JPG or .jpg will be processed
done

```

---

### Post by sisco311 on 2010-12-26
> **U2XS said:**
> Last question!

I would like the for loop to affect the .jpg as well as the .JPG files.  I tried, this, but it didn't work

```
for file in *.jpg || *.JPG; do 
echo Either .JPG or .jpg will be processed
done

```

The syntax is **for variable in list-of-words; do**, so:
```
for file in *.jpg *.JPG; do
```
should do the trick. A less portable variant is:
```
for file in *.{jpg,JPG}; do
```
If you want to match any combination of lower and upper case letters:
```
for file in *.[jJ][pP][gG]; do
```

---

### Post by U2XS on 2010-12-26
Thanks again.  I think I'll go with the last one.  Just to be sure that none fall through the cracks.  I presume that I can add formats to this one as well.  

```
for file in *.[jJ][pP][gG] *.[pP][nN][gG] *.[bB][mM][pP] *.[gG][iI][fF] *.[tT][iI][fF]; do
echo Process
done
```

P.S.  In addition to being very helpful, I think you're also a good teacher.  Seeing all of the options together helps me to understand the syntax/format which prevents me from asking future questions!

---

