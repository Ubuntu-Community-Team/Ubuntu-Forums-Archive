---
title: "remove duplicate lines in plain text file"
date: 2010-04-14
forum: General Help
---

### Post by Dayofswords on 2010-04-14
i have a big file of random numbers i generated at some point in time, after working with it with different things(how fun that was:P)... i want to remove duplicate lines and i'm not sure i'm doing this right

heres the command
```
sort random.txt | uniq -u > rand-shorter.txt

```
the file is pretty big, everything on a new line. i found the command on a web site so i'm sure its correct(bit of a command line in linux newbie)

can anyone confirm if this will remove lines duplicate lines (keeping one copy) and dump what is left in a file named rand-shorter.txt?


EDIT: i think its actually working, just taking a reallllly long time (on an old pen 4 from 2000)

---

### Post by dominiquec on 2010-04-14
uniq -u will only print the unique lines, which means that if you have a number occur more than once, it won't come out at all.  

That said, the command should work.  Why don't you try it out with a short test case for which you know the result?

---

### Post by jobix on 2010-04-14
If I understand you correctly, you want to remove duplicate lines but keep one, in which case you should not use the "-u" option. For example, if your text looks like this:

> hello
world
test
hello
ubuntu


sort file.txt | uniq -u 
will give you:
> test
ubuntu
world

sort file.txt | uniq 
will give you:
> hello
test
ubuntu
world


---

### Post by Dayofswords on 2010-04-14
thank you for the help, i'm now running it without the -u

did a small test(should have done it first :P) it worked how i want it too without the -u

now i wait for it to work...

i'm just going to say solved cuz the small test did what i want to big file to do, so all good

Thank you for the help 8)

---

### Post by kaibob on 2010-04-14
Sort has a -u option:

```
$ cat file
hello
world
hello
world
test

$ sort -u file
hello
test
world
```

---

### Post by Dayofswords on 2010-04-14
> **kaibob said:**
> Sort has a -u option:

```
$ cat file
hello
world
hello
world
test

$ sort -u file
hello
test
world
```
it seems to do the same thing as
```
sort blah | uniq
```
so would sort -u just be shorter?
(now trying to see if it works the same)

---

### Post by kaibob on 2010-04-14
If the file is very large, you may want to give awk a try:

```
awk ' !x[$0]++' file
```

This commmand has the possible advantage that it does not reorder the lines in file, which may or may not be a good thing. 

REFERENCE
[http://unstableme.blogspot.com/2008/03/remove-duplicates-without-sorting-file.html](http://unstableme.blogspot.com/2008/03/remove-duplicates-without-sorting-file.html)

---

### Post by Dayofswords on 2010-04-14
it finished and i check(via md5sum) that 

```
sort -u input.txt > output.txt
```
and
```
sort input.txt | uniq > output.txt
```
do the same thing

```

:~/Desktop$ md5sum rand-shorter.txt 
3be784ba9542568589c9b783d0f21365  rand-shorter.txt
:~/Desktop$ md5sum ./test/rand-shorter.txt 
3be784ba9542568589c9b783d0f21365  ./test/rand-shorter.txt

```
one on desktop is the sort input.txt | uniq > output.txt

the one in the test folder is sort -u input.txt > output.txt


so sort -u sound alot easier


Thank you to all those who have helped

to kaibob:
ordering doesnt matter here, but hey, nice to know (does it remove duplicates and leave one copy?)

---

### Post by kaibob on 2010-04-14
> **Dayofswords said:**
> to kaibob:
ordering doesnt matter here, but hey, nice to know (does it remove duplicates and leave one copy?)

The awk command does the same thing as the sort command except for the ordering. This is beyond my knowledge level, but I seem to recall reading somewhere that awk is generally faster when working with large files. That's the only reason I mentioned it.

---

