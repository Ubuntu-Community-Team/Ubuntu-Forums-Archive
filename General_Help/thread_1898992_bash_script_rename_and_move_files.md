---
title: "bash script rename and move files"
date: 2011-12-22
forum: General Help
---

### Post by hanskes on 2011-12-22
I have a question about bash scripting (sorry for my bad english)
 I have a large number of files in one folder in the name of 1a.jpg up to 500a.jpg, 1b.jpg to 500b.jpg, 1c.jpg to 500c.jpg and 1d.jpg to 500d.jpg. I want to create folders named ./1 and move the files 1a.jpg, 1b.jpg, 1c.jpg, 1d.jpg into it. Next, execute a number of commands over the files in this directory and go to the beginning of the script and move the files 2a.jpg, 2b.jpg, 2c.jpg and 2d.jpg to the next directory created by the script ./2 (and repeating the same commands as the first time) and so on to 500. Any idea how I can do this in a bash script?

---

### Post by searchfgold6789 on 2011-12-22
Here's how you can create the directories:
```

for (( i=1; i<501; i++ )); do mkdir dir$i; done                      
```

---

### Post by Vaphell on 2011-12-22
and moving files to directories would be
```
for f in *.jpg; do mv $f ${f%[abcd].jpg}; done
```
(assuming directories 1-500, not dir1-dir500 as in post above)

---

### Post by killermist on 2011-12-22
```
for iter in {1,2,3,4}\
{0,1,2,3,4,5,6,7,8,9}\
{0,1,2,3,4,5,6,7,8,9}\
 {1,2,3,4,5,6,7,8,9}\
{0,1,2,3,4,5,6,7,8,9}\
 {1,2,3,4,5,6,7,8,9} 500\
 do mkdir $iter; mv "$iter"{a,b,c,d}.jpg "$iter"\
 done

```(the way [end-of-line] markers are escaped is essential, or it won't work.  It DOES NOT look right in a code block otherwise.)
 that is creates directories for 100-499, 10-99, 1-9, and 500 
Then populates with files of said number plus a, b, c, d and .jpg extension.

Others can (and will, I'm sure) vouch that my use (abuse?) of known value expansion/iteration is correctly applied here.

---

### Post by Vaphell on 2011-12-23
what about
```
for iter in **{1..500}**
do
  ...
done
```
? :D

---

### Post by d2btoo on 2011-12-23
aha brace expansion then what's wrong with...
```
mkdir {1..500}
```

:-P :)

---

