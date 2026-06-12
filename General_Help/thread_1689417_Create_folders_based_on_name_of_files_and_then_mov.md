---
title: "Create folders based on name of files and then move to folder"
date: 2011-02-16
forum: General Help
---

### Post by younghat on 2011-02-16
Hi,

Im completely new to ubuntu or basically non-windows in general. I have a small problem Im sure some of you would find very easy to solve. I have a folder with MANY rar archives which are split (for eg. part1.rar, part2.rar). I would much prefer the archives having the same name (but diferent part nos) be copied into a folder with their name (but not extension). for eg:
Pics102000.part01.rar, part02.rar and so on.
Should be moved into a directory named: Pics102000.

And yes I want the rars in the directory, I dont want to extract them.

Any help appreciated

---

### Post by asmoore82 on 2011-02-16
The first thing that's addictive about the terminal is how quick it can be to
get to the far reaches of the filesystem. It's unbeatable for administrative tasks.

The next big step that is hard to live without is that it is scriptable
"on the fly" - any code that could be used in a shell script is also valid
to type right on the command line.

Something like this should do it:
```
for file in *.part*.rar
do
    if [ -f "$file" ]
    then
        stub="${file%%.*}"
        mkdir "$stub"
        mv -iv "$stub".* "$stub/"
    fi
done
```

---

### Post by younghat on 2011-02-17
Wow that was quick
I seem to be getting  syntax error
word unexpected (expecting: "do")

Im sure Im making some noobie mistake.

---

### Post by younghat on 2011-02-17
I would also like help in one more similar problem (even though Ive not been able to solve the other one yet):
When I rar a folder I would like to transfer the rar file (or files) to the folder itself.
For eg: lets say I have a folder DATA1 with a file abc.jpg.
It should create data1.rar (which would then have abc.jpg in it) and then move it into the (now empty) DATA1. So when I go into data1, there is only an archive (data1.rar), no non archived files.
Thanks a ton

---

