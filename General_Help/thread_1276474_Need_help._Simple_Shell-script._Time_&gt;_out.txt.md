---
title: "Need help. Simple Shell-script. Time &gt; out.txt"
date: 2009-09-27
forum: General Help
---

### Post by electronauts on 2009-09-27
Hey there. How can I make the script work?
Here is the damn peace of code.
```
function func_x()
{
echo `date`
sleep 1
echo `date`
sleep 1
echo `date`
sleep 1
}

time -f %e -o t_out.txt func_x
```

What it gotta do is to write info about running function-time to an external file. 

ThanX. :)

---

### Post by Psycho.mario on 2009-09-27
Why are you using a function?
You can do what you are trying to achieve in one line of [Messy] Commands:
```
echo `date`; sleep 1; echo `date`; sleep 1; echo `date`; sleep 1
```

If you assigned this to a variable:

```
function=`echo `date`; sleep 1; echo `date`; sleep 1; echo `date`; sleep 1`
```

Then you could just use $function to run those commands

---

### Post by electronauts on 2009-09-27
Well, I use the function because it's just a frame. 
Actually, there is a bulk of commands in a function that run for about 3-4 min.

I need to know the period of time of the running function, and I need it in a text output file. That's why I'm using `time` command.

Jst wonna focus Your attention on the problem with using time command in a shell-script. 

```

greg@ubuntu:~/Desktop$ cat test.sh
function func_x()
{
echo `date`
sleep 1
echo `date`
sleep 1
echo `date`
sleep 1
}

time -f %e -o tm.out func_x



greg@ubuntu:~/Desktop$ ./test.sh
./test.sh: line 11: -f: command not found

real    0m0.055s
user    0m0.000s
sys     0m0.032s
greg@ubuntu:~/Desktop$


```:guitar:

ThanX. ^^

---

### Post by DaithiF on 2009-09-27
time on its own executes the built-in shell command of that name, which doesn't take the options that the standalone program /usr/bin/time does.  So use the full path to the time command in your script ... /usr/bin/time -f % etc....

---

### Post by electronauts on 2009-09-27
ThankX!!! It worx now. ^^

---

