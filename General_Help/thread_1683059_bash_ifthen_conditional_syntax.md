---
title: "bash if/then conditional syntax"
date: 2011-02-06
forum: General Help
---

### Post by jadedcritic on 2011-02-06
OK - I pride myself on at least trying to help myself before I ask, but I've been staring at this a long time, I'm just not getting any traction.  Any guidance is certainly appreciated.

I've literally got 3 linux references on my desk right now that say that I should be able to use if conditionals, for example

[ -d FILE ]	True if FILE exists and is a directory.
[ -e FILE ]	True if FILE exists.
[ -f FILE ]	True if FILE exists and is a regular file.

Every time I try, I end up getting stuff like this
backup.sh: 14: [-d: not found

here's the statement that caused it

if [-d $1 -a -d $2]
then
cp $1/*$2

Attempts to use invoke it just at the regular prompt usually end up like this:

@fozzie:~/Documents$ if -f ~/Documents/testdoc then echo "file exists"; fi
bash: syntax error near unexpected token `fi'

Something is most likely wrong with my syntax here, but I will be snookered if I know what it is.

---

### Post by DaithiF on 2011-02-07
you need a space between the [ character and whatever test you are performing.

```
if [ -d somedir ]; then
   echo "it exists!"
fi

```

---

### Post by slooksterpsv on 2011-02-07
Also you need a ; (semi-colon) after the ]
And fi at the end.

---

### Post by sam1948 on 2011-02-07
just 1 tiny thing..
there are many "bash"s and they can be in the directories 
"/bin" or in "/user/bin"
or even more places

the "bash"s i know are:
/bin/sh 
/bin/bash
/bin/ksh
/bin/tcsh

and so on.
therefore when u r looking for scripting "howto"
see what "bash" r u using.

the popular in ubuntu is /bin/bash
that means u have to write 
#!/bin/bash
at the top line in u'r scripts

good luck

---

### Post by Vaphell on 2011-02-07
> **slooksterpsv said:**
> Also you need a ; (semi-colon) after the ]

true, but only if 'then' word is in 1 line with condition. you can skip that if you put 'then' in a new line.

---

### Post by jadedcritic on 2011-02-07
This is working well now, thank you all for input :D

My problem in a nutshell is that I've been trying to follow a bash scripting tutorial/example from a magazine, and they don't do a good job of explaining themselves or marking where the spaces need to be!

If folks are curious, here's the whole thing.

#!/bin/bash

if [ -d $1 -a -d $2 ]
then
cp $1/* $2
echo "backup complete"
elif [ -d $1 ]
then
mkdir $2
cp $1/* $2
echo "backup complete"
else
echo "unable to locate source directory"

---

### Post by glene77is on 2011-02-07
[QUOTE=jadedcritic;10435835]

Your first post had this code: 
cp $1/*$2
which is missing a space.
Should have been like this: 
cp    $1/*    $2


Is the magazine available on-line?
 Where are your variables defined? 

HTH

---

### Post by jadedcritic on 2011-02-07
I don't know if it's online or not; it's a special edition linux format.  linuxformat.com/tuxradar.com.   Don't know when it was published, copyright date says 2010 - but it seems like a huge chunk of the really good open source stuff gets done in EU, so I've grown accustomed to us not receiving things like this until 2-3 months after they're actually published. 

That's one of the things the tutorial didn't do a good job explaining.  Typeface doesn't really make it clear where the spaces need to go, but I was able to figure out where the variables come from, they need to be passed into it as arguments.

backup.sh "/foo" "/bar"

They use bourne shell too, at one point I actually tried running bourne to see if I could get it to work, but most of the reading I've been doing suggests fairly strongly that bash is directly descended from Bourne.   Therefore it's logical that most things that work in Bourne, should work in Bash.

---

