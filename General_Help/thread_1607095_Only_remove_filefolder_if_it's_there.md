---
title: "Only remove file/folder if it's there"
date: 2010-10-27
forum: General Help
---

### Post by inameiname on 2010-10-27
This is probably a very simple question and answer, so here goes...

Doing the basic:

```

rm -fv -R "FILE1" "FILE2" "FILE3" "FILE4" "FOLDER" "FILE_WHATEVER"

```

...works just fine, but I would like to know if there is a way to only remove if the files are actually there. Currently, I know of this format, which works just fine:

```

if [ -f "FILE1" ];then
    rm -fv -R "FILE1"
fi

```

...however, it seems to only work one file/folder at a time. Is there a way to modify it:

I tried this, but it didn't seem to work:

```

if [ -f "FILE1" "FILE2" "FILE3" "FOLDER" "WHATEVER" ];then
    rm -fv -R "FILE1" "FILE2" "FILE3" "FOLDER" "WHATEVER"
fi

```

---

### Post by gradysghost on 2010-10-27
I'm not a BASH scripting expert, but I do program, and the solution that seems most obvious to me would be to create a list/array of folders that you want to delete (or possibly get these from the command you call the script with) and run that same test on each directory.

Out of curiosity, though, why is the rm command bad for you?  To my knowledge, it doesn't crash out if a directory doesn't exist, only skips over it.

---

### Post by linux-hack on 2010-10-27
just make an array with your files and then make a for loop, like this,

```
files[0]= file_name1
files[1]= file_name2
files[2]= file_name3
files[3]= file_name4

for item in files;
do
   if [ -f "${item}" ];then
      rm -fv -R ${item}
   fi
done
```

---

### Post by inameiname on 2010-10-27
Oh, rm isn't bad for me. This is mostly out of boredom and curiosity. I was curious if it was possible to do this, that's all. You are right that it doesn't care really if a directory is there or not.


And thanks for the array example. I'll check it out.

---

### Post by inameiname on 2010-10-27
Oddly, this doesn't work, and I've tried with and without a space after '=':

```

#!/bin/bash


files[0]="/text1.txt"
files[1]="/text2.txt"
files[2]="/text3.txt"
files[3]="/text4.txt"
files[4]="/text5.txt"
files[5]="/text6.txt"


for item in files;
do
   if [ -f "${item}" ];then
      rm "${item}"
   fi
done

```

---

### Post by gradysghost on 2010-10-27
That may be because your code assumes the files live directly in the root directory, which I'm sure they don't.  Try adding dots to those filenames like this:

```
files[0]="./text1.txt"
files[1]="./text2.txt"
files[2]="./text3.txt"
files[3]="./text4.txt"
files[4]="./text5.txt"
files[5]="./text6.txt"
```

---

### Post by gradysghost on 2010-10-27
Of course, the more appropriate response is to ask to what extent it fails.  Assuming that some demo code has bad filenames in it seems like such a condescending thing to assume.

---

### Post by aromo on 2010-10-27
try this:
find /full_path -name 'FILE*' -exec rm -fv -R {} \;


For more file/folder selection options, run:
man find

Cheers

---

### Post by inameiname on 2010-10-27
Thanks, Gradysghost. I didn't think about adding a '.'. We'll see if that works.

Oh, and as to what happens when I run it, the terminal gives me no output at all, and along with that, in the folder where the script is, several blank files pop up and the computer gets partially frozen, and it takes a sec for that to go away. Yeah, not fun.

So, you are saying Aromo that this should work?:

```


#!/bin/bash

files[0]="/text1.txt"
files[1]="/text2.txt"
files[2]="/text3.txt"
files[3]="/text4.txt"
files[4]="/text5.txt"
files[5]="/text6.txt"

find /full_path -name 'FILE*' -exec rm -fv -R {} \;

```

UPDATE:


Unfortunately, I can't seem to get either to work.

---

### Post by inameiname on 2011-06-18
I'm curious if anybody ever figured out how to easily do this. Not a big deal for me now, as I figured out how to do whatever it was I needed this for (its been a while :P). I must've just worked around the problem.

---

