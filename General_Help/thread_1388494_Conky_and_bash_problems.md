---
title: "Conky and bash problems"
date: 2010-01-23
forum: General Help
---

### Post by Kruptein on 2010-01-23
okay so I have a line in my conky script:
```
${execi 10 /home/kruptein/test -s}
```

and in the test file I first had a function, but conky gave an error like:
Unknown tag: function
although in the shell it just works perfect without an error.

I was able to do it without a function, but now I need to use:
```
if [[ `ps ax | grep -v grep | grep opera` ]]; then ...
```
and conky gives the error: [[: not found

how does it come that conky can't handle [[ and functions?
but the terminal can

I hope you can help me.

---

### Post by pbrane on 2010-01-23
First can you post the bash script you are trying to run from conky.
Second you should rename the script to something other than 'test'. 'test' is already a bash builtin as well as a program on your system that checks file types. 

Also conky doesn't handle the script syntax itself, it just runs the script. If conky is giving you that error then it isn't running the script properly. Conky should just run the script and bash parses and executes the script.

---

### Post by Kruptein on 2010-01-23
The script:
```
#/bin/bash
if [[ `ps ax | grep -v grep | grep opera` ]]
then
	status='running'
else
	status='not running'
fi
while getopts s opt
do
    case "$opt" in
      s)  echo $status ;;
      \?) echo >&2 \
	  "usage: $0 [-s]"
	  exit 1;;
    esac
done
shift `expr $OPTIND - 1`
```

if I do:
```
if ps ax | grep -v grep | grep opera
```
then it does work but it also shows the output of ps, which is normal.

But if I run the same file from terminal it just outputs running without any error...

I also tried to rename it to tst but no luck either...

---

### Post by pbrane on 2010-01-23
You start the script with **#!***/bin/bash*. Naming the script something descriptive is generally better, like *check_opera*. What is the 's' argument to your script for?

Another way to test if opera is running is with:
```
 if [ "$(pidof opera)" ] 
```

---

### Post by Kruptein on 2010-01-24
I can't believe it was the "!" =D I looked trough whole my code except that line and couldn't find what is wrong.

Thanks a lot

And your way of checking if opera is running is much easier =D

But the opera thing was actually just as a test to see if I was able to let bash scripts echo their output to conky...

---

### Post by pbrane on 2010-01-24
Cool! I beleive that any app or script run in the .conkyrc that outputs to stdout (screen) will be redirected to the conky window output.

I've written scripts and apps that don't work only to find some small typo. I've looked through code for quite some time before seeing it.

---

### Post by teresaejunior on 2010-01-24
Sometimes it works better without [[]], try:

```
if pidof opera > /dev/null; then
  blabla
else
  blabla
fi
```

---

### Post by Kruptein on 2010-01-24
> **teresaejunior said:**
> Sometimes it works better without [[]], try:

```
if pidof opera > /dev/null; then
  blabla
else
  blabla
fi
```

Yes indeed with pidof it is much easier, but with the one I first had (the one with all the pipes | :D) I had to do it with [[ `...` ]] caus otherwise it would still output the ps command ;)

Nevermind you are right :)

---

### Post by teresaejunior on 2010-01-24
I was playing yesterday with a script, and it didn't work with [ `pidof opera` ], so I found that works better. Don't forget the > /dev/null. If you don't use it and run in the terminal, it will print the pid.

---

### Post by Kruptein on 2010-01-24
Okay, thanks

---

### Post by pbrane on 2010-01-24
> **teresaejunior said:**
> I was playing yesterday with a script, and it didn't work with [ `pidof opera` ], so I found that works better. Don't forget the > /dev/null. If you don't use it and run in the terminal, it will print the pid.

You don't need the backquotes. And the brackets redirect the output.

---

### Post by teresaejunior on 2010-01-24
yes i don't use them!

if pidof opera > /dev/null; then

---

