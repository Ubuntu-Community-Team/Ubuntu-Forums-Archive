---
title: "bash script for each line of input"
date: 2011-07-21
forum: General Help
---

### Post by chris1497 on 2011-07-21
I've written my script so that it reads in the variables $1 $2 $3 $3....$12

I have an input file as follows

word1 1 1 2 3 4 5
word2 1 1 2 3 4 5 6
word3 1 1 2 3 4

I would like to take the values from the input file and run the script once for each line.

i.e.

./script word1 1 1 2 3 4 5
./script word2 1 1 2 3 4 5 6
./script word3 1 1 2 3 4

please note that the numbers are not nessicarily in ascending order like this and their order is important.

sorry for the newb question. but I've looked around a bit and the solutions I found did not work for me.

---

### Post by sectshun8 on 2011-07-21
SO let me see if I understand.

You have an input file.. lets just say input.txt that has a value on each line.
You want the script to read the file, assign each line to a variable, and then run whatever process on each variable?

---

### Post by chris1497 on 2011-07-21
no I need to input each line into the script.  the script gets run one time for each line

./script line1

where line1 (word1 1 2 3 4....) automatically gets broken into

$1 -> word1
$2 -> 1
$3 -> 1
$4 -> 2
$5 -> 3
...etc

and the script uses these variable

---

### Post by nothingspecial on 2011-07-21
Scrub that then ^^^

---

### Post by chris1497 on 2011-07-21
scrub?

---

### Post by nothingspecial on 2011-07-21
I wrote how to take each line as a variable. When I saw your answer I scrubbed mine because it was wrong.

---

### Post by chris1497 on 2011-07-21
needlessly wasteful but is there a way to just cat each line to a file

ie

word1 1 2 3 4 5 -> vars1.txt
word 2 1 2 3 4 -> vars2.txt
word3 1 2 3 4 5 6 -> vars3.txt

then I could for loop across all the files cause the script works if I use cat and there is only one line

there should probably be a one liner for this, but its escaping me at the moment and I'm not running on much sleep

---

### Post by zero2xiii on 2011-07-21
Not the cleanest approach, but it might work?

Count the number of "words" in the line, then put each "word" on a new line, in a new temp file if you need to (you should be able to pipe it) then use that new file (or pipe) as a var per line.

---

### Post by zero2xiii on 2011-07-21
$ echo "cherry apple peach" | tr " " "\n"
cherry
apple
peach

Take this approach for each line, but pipe that into your program, or to a file with the ">". Then read the output file as a single line. Thus each line of the new file, will be a variable.

Then as the program executes further, line 2 of the original file, gets broken up again, and the new file is read again, and so it continues..


A few google searches gave some very decent results. Try it:
[http://www.linuxquestions.org/questions/linux-general-1/read-variables-from-a-text-file-in-bash-511760/](http://www.linuxquestions.org/questions/linux-general-1/read-variables-from-a-text-file-in-bash-511760/)

[http://mandrivausers.org/index.php?/topic/21998-reading-a-text-file-line-by-line-with-bash/](http://mandrivausers.org/index.php?/topic/21998-reading-a-text-file-line-by-line-with-bash/)

also do some research on CAT, GREP, SED etc... some of them you can truncate a file down to a line and coulom. Making the entire process more universal.

---

### Post by nothingspecial on 2011-07-21
```
for w in $(cat blah.txt); do echo $w >> blag.txt; done
```

Now each word is on a new line

```
while read l; do <fancy commands> "$l"; done< blag.txt
```

---

