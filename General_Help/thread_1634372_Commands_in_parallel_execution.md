---
title: "Commands in parallel execution"
date: 2010-11-30
forum: General Help
---

### Post by mynamehere on 2010-11-30
Hey there,

I've a bash script which simply executes several commands (running my own coded program "foo") one after the other in linear mode (passing one arguments each time):

foo 1 > log1
foo 2 > log2
foo 3 > log3
foo 4 > log4
....
foo N > logN

so they are executed one after the other. Now I wonder if it's possible to run them in parallel, so that all my cores are fully used (I've got 8 ones). I searched google and found 

[http://code.google.com/p/ppss/](http://code.google.com/p/ppss/)

but that's for files and I don't know how to executed such commands like mine with it. I also searched for a mpirun tutorial but couldn't get it to work with only 2 processes:

mpirun foo 1 : foo 2

Any help appreciated!

---

### Post by ron999 on 2010-11-30
Hi
Try the commands with **&** between them.
Like this:-

```
foo 1 > log1 &\
foo 2 > log2 &\
foo 3 > log3 &\
foo 4 > log4 &\
....
foo N > logN
```

---

### Post by mynamehere on 2010-11-30
Oh thanks, that works, but what doesn't work is:

START=$(date +%s)
foo 1 > log1 &
foo 2 > log2 &
foo 3 > log3 &
foo 4 > log4 &


END=$(date +%s)
DIFF=$(($END-$START))
echo "Took $DIFF Seconds!"

the measurement doesn't display anything :( is there any possibility to wait until each "foo"-process has ended and only than proceed with the command "END=..."?
thanks!

perhaps a while loop which runs as long as there's still a process with the name "foo" running or something like that :)!?

edit2: got it finally...

```
while [ 1 -gt 0 ]
do
  count=`ps ax | grep foo | grep -v grep -c`
  if [ $count -eq 0 ] 
    then
    break;
  fi
done
```

---

