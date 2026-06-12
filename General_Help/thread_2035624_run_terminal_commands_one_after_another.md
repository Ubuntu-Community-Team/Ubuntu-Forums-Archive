---
title: "run terminal commands one after another"
date: 2012-07-31
forum: General Help
---

### Post by mich3lam on 2012-07-31
let's say i have those 5 commands, is there is a way to make them run automatically one after another?
example:
COMMANDS ONE
*FINISHED*
COMMANDS TWO
*FINISHED*
COMMANDS THREE

etc...

---

### Post by vexorian on 2012-07-31
echo "hello" && echo "sad" && echo "world"

due to && being a lazy operator (it is the AND operator) if a command fails, the next one won't run.

---

### Post by mich3lam on 2012-07-31
thanks a lot for your fast response!

---

### Post by Megaptera on 2012-07-31
Further to vexorian's answer ... this 
Quote  "Want to know how to run two or more linux commands sequentially? It's simple: use the semicolon ;.
For instance:

cd;ls

This will change the directory to your home directory, then list the contents. You can use as many semicolons as you wish.

Another option is to use && if you only want the next command to execute if the previous command executed successfully.

cd ~/myfiles; cp file.txt ~/backup/ && rm file.txt

This will only run the last command if the cp command executed successfully.

You can swap the && for || to run a command if the previous one fails." End quote

From here: [http://breckyunits.com/code/run_multiple_commands_at_once](http://breckyunits.com/code/run_multiple_commands_at_once)

---

### Post by mich3lam on 2012-08-01
I have already asked this question and got an answer but I could not get it to work.
Let's say I want to run few commands in terminal one after another.

I would really appreciate it if you give me an example with those three commands:

1)
```
mencoder 1.avi -sub 1.srt -subcp Windows-1255 -subfont "DejaVu Sans" -subfont-text-scale 4 -subfont-outline 1 -ovc xvid -oac mp3lame -xvidencopts pass=1 -o 11.avi
```

2)
```
mencoder 2.avi -sub 2.srt -subcp Windows-1255 -subfont "DejaVu Sans" -subfont-text-scale 4 -subfont-outline 1 -ovc xvid -oac mp3lame -xvidencopts pass=1 -o 22avi
```

3)
```
mencoder 3.avi -sub 3.srt -subcp Windows-1255 -subfont "DejaVu Sans" -subfont-text-scale 4 -subfont-outline 1 -ovc xvid -oac mp3lame -xvidencopts pass=1 -o 33.avi
```

It'll be easier for me to learn it this way.

Thanks a lot!

---

### Post by beboylips on 2012-08-01
Hi,

I would use a shell script:

```

#!/bin/bash

command 1
command 2
command 3


```

Save it as script.sh, cd to the directory where you saved it and
```

chmod +x script.sh

```
and
```

./script.sh

```

-Beboy

---

### Post by idoitprone on 2012-08-01
if you want it on one line


use ; or &&

&& will run if previous command suceed

; is another way to seperate commands just like using return key

```
comand1 && command2 && command 3
```

or 

```
command1; command2
```

---

### Post by oldos2er on 2012-08-01
Threads merged. Please don't start more than one thread per topic.

---

