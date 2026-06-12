---
title: "[bash] how to change the name of file in many folders"
date: 2011-08-02
forum: General Help
---

### Post by ziemowitzima on 2011-08-02
Hello,
I faced such problem recently :
I have a folder *results* and in this folder I have set of folders named:
[I]1050.2000
1050.4000
...
1098.8000
1100.0000[/I]

in each of this folders there is file: *(1_d)wu_z*
I need to write a bash script which would change the name of this file (in every folder) to: *wu_z*

The main problem here seems to be, how to "decrease/change" the folder name by 0.2000 in the loop...

Thanks for your help!
-ZM

---

### Post by AlphaLexman on 2011-08-02
> **ziemowitzima said:**
> in each of this folders there is file: *(1_d)wu_z*
I need to write a bash script which would change the name of this file (in every folder) to: *wu_z*

The main problem here seems to be, how to "decrease/change" the folder name by 0.2000 in the loop...

Thanks for your help!
-ZM
You can do it in a one-liner...
Just go to the parent directory and copy my code in a terminal.
```
find . -name "(1_d)wu_z" -exec rename [COLOR="Red"]-n[/COLOR] 's!\(1_d\)!!' {} +
```
Remove the '-n' to actually execute the code.

---

### Post by ziemowitzima on 2011-08-02
Thank you !

---

### Post by AlphaLexman on 2011-08-02
Glad to help!

Please use the Thread Tools to mark the thread as Solved.

---

### Post by nothingspecial on 2011-08-02
Since we already know where the files are we don't need find. From the results directory

Check with

```
for f in */\(1_d\)wu_z; do echo "${f/(1_d)/}"; done
```

Do it with

```
for f in */\(1_d\)wu_z; do mv "$f" "${f/(1_d)/}"; done
```

Not trying to be funny, but if there were 10s of thousands of files, that would speed things up considerably.

:)

---

### Post by ziemowitzima on 2011-08-24
Thanks a lot !
Now I am trying sth different and I have some difficulties...
I need to copy a file named "u_ss", which is in many different folders:
one\1000.0000
one\1001.0000
...
one\1050.0000

to a same named folders but in different location:
two\1000.0000
two\1001.0000
...
two\1050.0000

Thanks in advance !
-ZM

---

### Post by sisco311 on 2011-08-24
Try something like:
```
shopt -s nullglob
cd /path/to/dir/one || exit 1

for file in */u_ss
do
    dirname="${file%/*}"
    **echo** cp -b -- "$file" "../two/$dirname"
done

```

delete the echo command to actually cp the files.

---

### Post by ziemowitzima on 2011-08-24
Thanks a lot !
It works perfect.
But there is one thing in the script above I dont understand:
How it knows that file u_ss should be copied form the folder e.g. 1010.000 to the same-named folder ?

---

### Post by sisco311 on 2011-08-24
The result of expanding the glob (*/u_ss) is this:
for file in "1001.0000/u_ss" "1002.0000/u_ss" "1003.0000/u_ss" and so on. Where 1001.0000, 1002.0000 ... are the names of the directories from the *one* directory.

**for variable in words** means: repeat the loop for each word, setting *variable* to each word in turn.

So, at the first iteration the value of *file* is set to "1001.0000/u_ss", at the second one is set to "1002.0000/u_ss" and so on.

The expression ${file%/*} cuts off everything from the end of the value of *file* starting with the last slash (/). In our case this is the name of the directory.

This value is assigned to the dirname variable, which later is used in the cp command.

Hope this makes sense to you. :)

---

### Post by ziemowitzima on 2011-08-25
Thanks a lot !
It makes perfect sens.
-ZMM

---

